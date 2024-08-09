# BES headphones firmwares (恒玄方案耳机固件)

## Background

The release of the v0027 firmware has rendered most AirPods clones based on the BES2500YP solution unusable due to an uncontrollable maximum volume issue. Since BES2500YP production has been discontinued, there is no official fix available. It's suspected that the v0027 firmware was intentionally released to obsolete older products.

Through my experiments, I found that the v0025 firmware, released in December 2022, does not suffer from this volume issue. Therefore, downgrading to v0025 is currently the best solution for BES2500YP devices.

v0027 固件发布后，大多数基于 BES2500YP 方案的 AirPods 仿品由于无法控制的最大音量问题而变得无法使用。由于 BES2500YP 已停止生产，因此没有官方修复方案。有传言称，v0027 固件的发布是为了故意淘汰旧产品。

通过我的实验，我发现 2022 年 12 月发布的 v0025 固件没有这个音量问题。因此，降级到 v0025 是目前解决 BES2500YP 设备问题的最佳方案。

## How to use

### 1. Download the BES app

For iOS users, go to App Store and search for "Hbluetooth" app.

For Android users, download the app called "Beehool" from here: https://caishenerji-1311175286.cos.ap-shanghai.myqcloud.com/web/_beehool.html.

### 2. Spoof the app for update (force)

The app will request their backend server for possible update, here's a example respond: 

```json
{
	"code": 0,
	"data": {
		"chipmodel": "BES2500YP",
		"describe": "优化蓝牙稳定性",
		"findtype": 0,
		"hardware": "hts121_v9_2500yp_v3_hf_yx_yx13mm",
		"id": 692,
		"productId": "3",
		"productName": "三代Pro(13mm)",
		"type": 1,
		"url": "https://caishenerji-1311175286.cos.ap-shanghai.myqcloud.com/ota/bin/2024-07-20/hts121_v9_2500yp_v3_hf_yx_yx13mm_SVN64707_V0027.bin",
		"version": 27
	},
	"message": "",
	"queryId": "",
	"total": 0
}
```
Use debugging proxy apps like Charles / Fiddler to capture and rewrite the update check request, change the URL of firmware to point to GitHub, also need to change the "version" property to 28, so that the app will consider this as an update and popup a notification. Like below,


```json
{
	"code": 0,
	"data": {
		"chipmodel": "BES2500YP",
		"describe": "优化蓝牙稳定性",
		"findtype": 0,
		"hardware": "hts121_v9_2500yp_v3_hf_yx_yx13mm",
		"id": 692,
		"productId": "3",
		"productName": "三代Pro(13mm)",
		"type": 1,
		"url": "https://github.com/gekowa/BES-Firmwares/blob/main/BES2500YP/BeePro-v3/hts121_v9_2500yp_v3_hf_yx_yx13mm_SVN63758_V0025.bin?raw=true",
		"version": 28
	},
	"message": "",
	"queryId": "",
	"total": 0
}
```

### 3. Do the "update"

After step 2, the app should popup a firmware upgrade notification when launched, perform the upgrade as normal.

### Limitation

Currently, only v0025 version firmware for BeePro v3 (红蜂三代Pro) was provided.

### Caution

If there's no issue using your device, please **DO NOT** update.

## Contribute
