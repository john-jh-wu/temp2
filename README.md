# # 文件

## 流程圖
<img width="665" alt="截圖 2025-02-10 下午1 39 39" src="https://github.com/user-attachments/assets/30dbdcd4-f2e7-4109-b9f8-2b715d710699" />

## 实时对话式 AI API 與相關文件
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

## 实时字幕
* [文件](https://www.volcengine.com/docs/6348/1337284)

> 在 StartVoiceChat 接口中配置 SubtitleConfig 结构体参数后，你可以开启房间内字幕回调功能。
> 服务端通过设定的 ServerMessageUrl 按照每句话返回字幕结果，你可以用来存储分析对话数据。

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

