# 文件

## 流程圖
<img width="661" alt="截圖 2025-02-10 下午2 58 56" src="https://github.com/user-attachments/assets/fa530504-7d4f-4c9c-b870-1a01866955f7" />


## 实时对话式 AI API 相關文件
* [文件](https://www.volcengine.com/docs/6348/1315560)
  * [启动智能体 StartVoiceChat](https://www.volcengine.com/docs/6348/1404673)
  * [更新智能体 UpdateVoiceChat](https://www.volcengine.com/docs/6348/1404671)
  * [关闭智能体 StopVoiceChat](https://www.volcengine.com/docs/6348/1404672)
* 音色列表
  * [大模型](https://www.volcengine.com/docs/6561/1257544)
  * [小模型](https://www.volcengine.com/docs/6561/97465)

## 術語
* app id
  * [控制台/实时音视频/应用管理](https://console.volcengine.com/rtc/listRTC)
* room id
  * room id 對應到我們內部系統的 conversation id 
* task id
  * TaskId 是任务的标识，在一个 AppId 的 RoomId 下 TaskId 是唯一的，不同 AppId 或者不同 RoomId 下 TaskId 可以重复，因此 AppId + RoomId + TaskId 是任务的唯一标识，可以用来标识指定 AppId 下某个房间内正在运行的任务，从而能在此任务运行中进行更新或者停止此任务。 
* token (for joining room)
  * 需由 Sever 返回。
* user id
  * user id (火山) 對應到我們內部系統的 user id。  

## 參數

### StartVoiceChat
```json
{
  "AppId": "678ef3c6ca9e3501ea3b12d0", // 填入專案所需
  "RoomId": "1", // 填入專案所需
  "TaskId": "2", // 填入專案所需
  "Config": {
    "InterruptMode": 0, 
    "ASRConfig": {
      "Provider": "volcano",
      "ProviderParams": {
        "Mode": "bigmodel",
        "AppId": "2829910511",
        "AccessToken": "zcuZ7uUqiLYvzrpTuhjXP-iJ9u4mYM0H",
      },
      "VolumeGain": 0.3,
    },
	"TTSConfig": {
	  "Provider": "volcano",
	  "ProviderParams": {
    	"app": {
	      "appid": "2829910511",
    	  "cluster": "volcano_tts",
	    },
    	"audio": {
	      "voice_type": "BV138_streaming",
    	}
	  }
	},
    "LLMConfig": {
      "Mode": "ArkV3",
      "EndPointId": "ep-20250124154348-rrrg2",
      "MaxTokens": 1024,
      "Temperature": 0.1,
      "TopP": 0.3,
      "SystemMessages": ["you can speak only English."], // 填入專案所需
      "UserMessages": [], // 填入專案所需
      "HistoryLength": 6, // 填入專案所需
    },
    "SubtitleConfig": {
      "SubtitleMode": 0,
    },
  },
  "AgentConfig": {
    "TargetUserId": ["2"], // 填入專案所需
    "WelcomeMessage": "Hey there, I'm Hendrix and I'm super into K-pop and making TikToks. What kind of music are you into these days?", // 填入專案所需
    "UserId": "Hendrix", // 填入專案所需
    "EnableConversationStateCallback": true,
  }
}
```

### UpdateVoiceChat - 傳送文字訊息
```json
{
    "AppId": "678ef3c6ca9e3501ea3b12d0", // 填寫專案所需
    "RoomId": "1", // 填寫專案所需
    "TaskId": "2", // 填寫專案所需
    "Command": "ExternalTextToLLM",
    "Message": "message", // 填寫專案所需
    "InterruptMode": 2
}
```

### UpdateVoiceChat - 打斷 Bot
```json
{
    "AppId": "678ef3c6ca9e3501ea3b12d0", // 填寫專案所需
    "RoomId": "1", // 填寫專案所需
    "TaskId": "2", // 填寫專案所需
    "Command": "interrupt"
}
```

## 其他
* Server 需要提供 API 讓客戶端打斷 Bot
* Server 需要提供 API 讓客戶端傳送文字訊息
* Server 需要提供 API 讓客戶端調整 Bot 語速

