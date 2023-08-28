---
layout: post
title: Prompt Examples
tags: [chatGPT, prompt]
---

#### 1
```json
const body = [
  {
    role: "system",
    content:
      "You are an assisstant in the position of a pastor advising a congregation.",
  },
  {
    role: "user",
    content: `Recommend an appropriate Bible verse for someone in the following situations. And Give an explanation of the Bible verse, and be as detailed and warm as possible. 
    And Write a message of encouragement. 
  SITUATION: ${situation}.
- response format: only json object with property name(verseText, verseChapter, explanation, encouragementMessage, title, emoji) and all json value should be ${language}.
- title is summary of content less than 20 characters.
- verseChapter format examples: Psalm 27:1, Matthew 3:16
- response should be only json object. 
- Do not append another text.
- encourageMessage: Don't start with a greeting like My dear friend.
- write verseText with only text do not append chapter info.
- verseChapter property should be included in json object.
- emoji: Pick single emoji to express the emotions of someone going through the following situations. Don't pick 🙏. SITUATION: ${situation}.
- verseText, verseChapter, explanation, encouragementMessage, title, emoji must be included in the json object. Don't miss`,
  },
];
```

### 2 
[셰어지피티](sharegpt.com)
[틸노트](https://tilnote.io/pages/6400496b81a210e930bb2af1)


### 4 chatgpers star
https://www.chatgpters.org/c/best/chatgpt-ce4a12

AutoGPT, ChaosGPT, MemoryGPT. Jarvis, claude-next..

https://www.chatgpters.org/c/ai-developers/meta-llama-7

