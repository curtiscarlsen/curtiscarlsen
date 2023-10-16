from gpt4all import GPT4All  
  
  
class StoryContext:  
    def __init__(self, cast, genre, pacing, format, style):  
        self.context = """  
story context: cast of characters: {}  
story genre: {}  
story pacing: {}  
story format: {}  
story style: {}  
        """.format(cast, genre, pacing, format, style)  
    def getPromptText(self):  
        return self.context  
  
class StoryOutline:  
    """create a list of outline elements, ID'd by dotted numeric indices"""  
    def __init__(self, outline_list):  
        self.outline = self.makeOutline(outline_list)  
  
    def makeOutline(self, outline_list, starting_key = None):  
        if not starting_key is None:  
            return [ [starting_key + "." + str(idx), item] for idx, item in enumerate(outline_list)]  
        else:  
            return [ [str(idx), item] for idx, item in enumerate(outline_list)]  
  
    def addItems(self, outline_list, starting_key):  
        for idx, pair in enumerate(self.outline):  
            if pair[0] == starting_key:  
                next_key = self.outline[idx+1][0]  
                if next_key.startswith(starting_key):  
                    new_outline = self.outline[0:idx] + makeOutline(outline_list) + self.outline[idx:-1]  
                else:  
                    new_outline = self.outline[0:idx] + makeOutline(outline_list) + self.outline[idx:-1]  
  
    def indexWithKey(self, key):  
        for idx, pair in enumerate(self.outline):  
            if pair[0] == key:  
                return idx  
        return None  
    def getPromptText(self, start_key= None, end_key = None):  
        if start_key is None:  
            skey = 0  
        else:  
            skey = self.indexWithKey(start_key)  
            if skey is None:  
                skey = 0  
  
        if end_key is None:  
            pairs = "\n".join(["{}: {}".format(key, item) for key, item in self.outline[skey:]])  
        else:  
            ekey = self.indexWithKey(end_key)  
            if ekey is None:  
                pairs = "\n".join(["{}: {}".format(key, item) for key, item in self.outline[skey:]])  
            else:  
                pairs = "\n".join(["{}: {}".format(key, item) for key, item in self.outline[skey:ekey]])  
  
        return "context outline: \n" + pairs + "\nend context outline\n"  
  
class Story:  
    def __init__(self, context, outline, narrative):  
        self.context = context  
        self.outline = outline  
        self.narrative = narrative  
    def getUpdatePrompt(self, narr_segment):  
        prompt = """Prompt: You are an AI text generator.  Write a paragraph based on the  inspiration that implements the focused outline elements in the context outline, in the context genre, format and pacing.  Extend the text with minor details and improved wording.  
"""  
  
        prompt += self.context.getPromptText()  
        prompt += self.outline.getPromptText()  
        prompt += self.narrative.getPromptText(narr_segment)  
        return prompt  
  
class NarrativeSegment:  
    def __init__(self, outline_elements_list, text):  
        self.outline_elements = outline_elements_list  
        self.text = text  
  
class Narrative:  
    def __init__(self, narrative_segments):  
        self.segments = narrative_segments  
  
    def getPromptText(self, seg_num):  
        seg = self.segments[seg_num]  
        prompt = "outline focus elements: {}\n".format(",".join(seg.outline_elements))  
        prompt += "inspiration: {}".format(seg.text)  
        return prompt  
  
o = StoryOutline(["a sunny day", "a rainy day", "The world ends"])  
context = StoryContext(["dogs", "cats"], genre="comedy",pacing="fast", format="novel", style="absurd")  
  
s = Story(context=context, outline=o, narrative = Narrative([NarrativeSegment(["1, 2"], """The day was bright and sunny.""")]))  
print (o.getPromptText())  
print (context.getPromptText())  
  
print ("story prompt: ", s.getUpdatePrompt(0) )  
  
# model = GPT4All('ggml-Wizard-Vicuna-7B-Uncensored.ggmlv3.q4_1.bin')  
# system_template = 'A chat between a curious user and an artificial intelligence assistant.'  
# # many models use triple hash '###' for keywords, Vicunas are simpler:  
# prompt_template = 'USER: {0}\nASSISTANT: '  
# with model.chat_session(system_template, prompt_template):  
#     response1 = model.generate('why is the grass green?')  
#     print(response1)  
#     print()  
#     response2 = model.generate('why is the sky blue?')  
#     print(response2)