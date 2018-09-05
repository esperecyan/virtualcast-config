VirtualCast/config.yaml
=======================
`config.yaml` (または `config.yml`) を `config.json` に変換後、VirtualCast.exe を起動する[WSH]スクリプトです。

[WSH]: https://ja.wikipedia.org/wiki/Windows_Script_Host "Windows Script Hostとは、Microsoft Windowsにおいてテキストファイルに記述したスクリプトを実行するスクリプト実行環境である。"

例
---
`VirtualCast.exe` があるフォルダに次のような `config.yaml` を置いておくと、

```yaml
niconico:
    character_models: # 利用するVRMモデルのニコニ立体番号
        - 32797 # ニコニ立体ちゃん (VRM) <https://3d.nicovideo.jp/works/td32797>
        - 32947 # 【VRM】まついしゃちょー <https://3d.nicovideo.jp/works/td32947>
        - 36346 # 【VRM】おの副社長 <http://3d.nicovideo.jp/works/td36346>
panorama:
    urls: # 背景で使うパノラマ画像のURL
        - 'https://www.virtualcast.jp/download/panoramas/IL_entrance.JPG'
        - 'https://www.virtualcast.jp/download/panoramas/chromakey.jpg'
        - 'https://www.virtualcast.jp/download/panoramas/chromakey_white.jpg'
whiteboard:
    urls: # ホワイトボードで使用する画像のURL
        - 'https://www.infiniteloop.co.jp/special/iltan/kabegami/infiniteloop-iltan-red-1024x768.jpg'
        - 'https://www.infiniteloop.co.jp/special/iltan/kabegami/infiniteloop-iltan-blue-1024x768.jpg'
        - 'https://www.infiniteloop.co.jp/special/iltan/kabegami/infiniteloop-iltan-pop-1024x768.jpg'
        - 'https://www.infiniteloop.co.jp/special/iltan/kabegami/infiniteloop-iltan-sd-1024x768.jpg'
cue_card:
    urls: # カンペで使用する画像のURL
        - 'https://www.infiniteloop.co.jp/special/iltan/kabegami/infiniteloop-iltan-red-1024x768.jpg'
        - 'https://www.infiniteloop.co.jp/special/iltan/kabegami/infiniteloop-iltan-blue-1024x768.jpg'
        - 'https://www.infiniteloop.co.jp/special/iltan/kabegami/infiniteloop-iltan-pop-1024x768.jpg'
        - 'https://www.infiniteloop.co.jp/special/iltan/kabegami/infiniteloop-iltan-sd-1024x768.jpg'
# ダイレクトビューモードで凸を受け入れるかどうか
allow_direct_view: true
```

次のような `config.json` に変換されます。

```json
{
	"niconico": {
		"character_models": [
			32797,
			32947,
			36346
		]
	},
	"panorama": {
		"urls": [
			"https://www.virtualcast.jp/download/panoramas/IL_entrance.JPG",
			"https://www.virtualcast.jp/download/panoramas/chromakey.jpg",
			"https://www.virtualcast.jp/download/panoramas/chromakey_white.jpg"
		]
	},
	"whiteboard": {
		"urls": [
			"https://www.infiniteloop.co.jp/special/iltan/kabegami/infiniteloop-iltan-red-1024x768.jpg",
			"https://www.infiniteloop.co.jp/special/iltan/kabegami/infiniteloop-iltan-blue-1024x768.jpg",
			"https://www.infiniteloop.co.jp/special/iltan/kabegami/infiniteloop-iltan-pop-1024x768.jpg",
			"https://www.infiniteloop.co.jp/special/iltan/kabegami/infiniteloop-iltan-sd-1024x768.jpg"
		]
	},
	"cue_card": {
		"urls": [
			"https://www.infiniteloop.co.jp/special/iltan/kabegami/infiniteloop-iltan-red-1024x768.jpg",
			"https://www.infiniteloop.co.jp/special/iltan/kabegami/infiniteloop-iltan-blue-1024x768.jpg",
			"https://www.infiniteloop.co.jp/special/iltan/kabegami/infiniteloop-iltan-pop-1024x768.jpg",
			"https://www.infiniteloop.co.jp/special/iltan/kabegami/infiniteloop-iltan-sd-1024x768.jpg"
		]
	},
	"allow_direct_view": true
}
```

使い方
------
![](demo.gif)

1. [バーチャルキャストを起動.js.cmd]を `VirtualCast.exe` があるフォルダに保存します。
2. `バーチャルキャストを起動.js.cmd` をダブルクリックして実行します。
3. `config.json` の内容をもとに `config.yaml` が作成された後、バーチャルキャストが起動します。  
   **※記述しているニコニ立体番号が多い場合、`config.yaml` の作成にしばらくかかります。**
4. `config.yaml` が存在する場合、変換して `config.json` に上書き保存され、その後バーチャルキャストが起動します。
5. `VirtualCast.exe` を直接起動する代わりに、常に `バーチャルキャストを起動.js.cmd` からバーチャルキャストを起動するようにしておくと、
   `config.json` の更新を意識せずにすむため便利です。

[バーチャルキャストを起動.js.cmd]: https://esperecyan.github.io/virtualcast-config/%E3%83%90%E3%83%BC%E3%83%81%E3%83%A3%E3%83%AB%E3%82%AD%E3%83%A3%E3%82%B9%E3%83%88%E3%82%92%E8%B5%B7%E5%8B%95.js.cmd

起動オプション
--------------
### `--esperecyan-niconico-character-models-offset-16x=[数字]`
`niconico.character_models` の順番をズラします。

例:

```yaml
niconico:
    character_models:
        - 32797
        - 32806
        - 32813
        - 32819
        - 32830
        - 32865
        - 32872
        - 32876
        - 32898
        - 32899
        - 32928
        - 32947
        - 32952
        - 32969
        - 33010
        - 33028
        - 40000
        - 40001
        - 40023
        - 40051
        - 40077
        - 40093
        - 40258
        - 40363
        - 40463
        - 40480
        - 40481
        - 40524
        - 40567
        - 40624
        - 40660
        - 40677
        - 41036
```

#### `--esperecyan-niconico-character-models-offset-16x=0` の場合
指定しなかった場合と同じ。

#### `--esperecyan-niconico-character-models-offset-16x=1` の場合

```json
{
	"niconico": {
		"character_models": [
			40000,
			40001,
			40023,
			40051,
			40077,
			40093,
			40258,
			40363,
			40463,
			40480,
			40481,
			40524,
			40567,
			40624,
			40660,
			40677,
			41036,
			32797,
			32806,
			32813,
			32819,
			32830,
			32865,
			32872,
			32876,
			32898,
			32899,
			32928,
			32947,
			32952,
			32969,
			33010,
			33028
		]
	}
}
```

#### `--esperecyan-niconico-character-models-offset-16x=2` の場合

```json
{
	"niconico": {
		"character_models": [
			41036,
			32797,
			32806,
			32813,
			32819,
			32830,
			32865,
			32872,
			32876,
			32898,
			32899,
			32928,
			32947,
			32952,
			32969,
			33010,
			33028,
			40000,
			40001,
			40023,
			40051,
			40077,
			40093,
			40258,
			40363,
			40463,
			40480,
			40481,
			40524,
			40567,
			40624,
			40660,
			40677
		]
	}
}
```

Contribution
------------
Pull Request、または Issue よりお願いいたします。

ライセンス
----------
当アドオンのライセンスは [Mozilla Public License Version 2.0] \(MPL-2.0) です。

JavaScriptオブジェクトとYAML文字列の相互変換に次のライブラリを埋め込んでいます。

- [js-yaml] — [MIT License]
- [es5-shim] — [MIT License]

[Mozilla Public License Version 2.0]: https://www.mozilla.org/MPL/2.0/
[js-yaml]: https://github.com/nodeca/js-yaml
[es5-shim]: https://github.com/es-shims/es5-shim
[MIT License]: https://ja.osdn.net/projects/opensource/wiki/licenses/MIT_license
