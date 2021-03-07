----------------------------------------
// 2076 by Yor
Added: extra system. What is it?
- it a system managed by map-server to add/remove zenys/items to/from characters.
- map-server use save/map_extra.txt file and manage it alone.
- to add a line in this file, use an other file (default: ./map_extra_add.txt; you can choose location and name of this file). map-server will check it every minute.
- because map-server READ and DESTROY this file, be sure that map-server has all permissions.
- When a character is online, map-serverwill do supposed actions (and check all: weigth, max values, etc...)
- To have more informations, read save/map_extra.txt file after a start of the map-server.
- you can disable this function by a option in map_athena.conf.
- The name? Because it's extra bonus/malus.
- Example of usages: on web site (bonus after an action), to remove easyly some items from a character (sprite error?), etc...
9 modified files:
	Readme2060
	(conf/)
		battle_athena.conf
		map_athena.conf
		msg_athena.conf
	(src/map/)
		battle.c
		battle.h
		map.c
		map.h
		pc.c

----------------------------------------
// 2075 by ARIA
・ASPDの最大値をPK,GVG,PVPで個別に制限できるように追加
	(conf/)
		battle_athena.conf
	(src/map/)
		battle.c
		battle.h
		status.c
----------------------------------------
// 2074 by Yor
Changed: GuildChangePositionInfo structure. guild_change_position can be use without the leader (create a GM command?).
Improved: GuildRequestInfo. do check in one place, and don't search sometimes twice the guild structure
5 modified files:
	Readme2060
	(src/map/)
		clif.c
		clif.h
		guild.c
		guild.h

----------------------------------------
// 2073 by Filia
・フルアドレナリンラッシュが遠距離攻撃に反映されている点を修正。
・生命力変換がSP_MAXでは使用出来ないように修正
　（本鯖相違スレッド４ 20 より）
　使用できない状況で使用失敗メッセージが出る・出ないが分からないので
　とりあえず使用失敗メッセージが出るようにしてあります
	Readme2060
	(db/)
		skill_require_db.txt
	(src/map/)
		skill.c
		status.c
----------------------------------------
// 2072 by luc
・スキル射程の見直し
・pet_db.txtの誤字を修正
・NPCスクリプトの修正
	(npc/town)
		npc_town_ayothaya.txt
		npc_town_kafra.txt
	(npc/job)
		npc_job_05merchant.txt
		npc_job_10blacksmith.txt
		npc_job_16sage.txt
	(warp)
		npc_warp_fild.txt
	thanks to AthenaDev

----------------------------------------
// 2071 by Yor
Improved: change_position in guild: check index.
Fixed: Only guild master can change position.
5 modified files:
	Readme2060
	(src/map/)
		clif.c
		guild.c
		intif.c
		intif.h

----------------------------------------
// 2070-fix by Yor
Fixed/improved: name in guild creation when @guild is used (guild_create in guild.c).
2 modified files:
	Readme2060
	(src/map/)
		guild.c
----------------------------------------
// 2070 by Yor
Checked: name in guild creation (guild_create in guild.c).
Improved: calls of (most) functions in guild.c/h.
Renamed: some 'index' variables to 'idx' variables.
7 modified files:
	Readme2060
	(src/map/)
		clif.c
		clif.h
		guild.c
		guild.h
		intif.c
		intif.h

----------------------------------------
//2069 by Rayce

・2067のMAX_SKILLの判定順がミスってたのを修正（pc.c）
		pointed out by Yor, thx a lot!!
・2068のbattle_config.gvg_flee_penaltyの処理を巻き戻し（status.c）
・カード効果によるコーマおよび即死が機能してなかったバグを修正（battle.c）

----------------------------------------
//2068 by ARIA

・MCの上限制限をPK,PVP,GVGでそれぞれbattle_athena.confで決めれるように追加

----------------------------------------
//2067 by Rayce

・pc.c, unit.cの処理改善
・skill_unit_db.txtの説明をdoc/db_ref.txtに記述
・skill.cのskill_misfire.txtとskill_prohibition_zone.txtに関する読み込み
　部分のコメントアウトを抹消
・clif.cからdb.hのincludeを削除（2064のやり残し）
・GvGマップでアンティペインメントを使用不可にする処理をpc.cから切り離して
　db/item_prohibition_zone.txtで制御するように変更
・クローンスキルの判定をダメージ発生前に移動
	battle_skill_attack()

----------------------------------------
//2066 by luc
・エラー E2313 clif.c 5778: 定数式が必要(関数 clif_showvendingboard )
・エラー E2313 clif.c 5801: 定数式が必要(関数 clif_closevendingboard )
コンパイル中に上記のエラーが出るため、clif.cの一部の巻き戻し。
----------------------------------------
//2065 by luc
・NPCスクリプトの修正
	(npc/town)
		npc_town_alberta.txt
		npc_town_guide.txt
	(npc/quest)
		npc_event_dye.txt
	thanks to AthenaDev

----------------------------------------
//2064 by Rayce

・add_timer() に起因するメモリリーク対策としてadd_timer2() を追加（timer.*）
　サーバプログラム終了時にタイマー待機中のデータをtimer.c内部でfreeします
	battle_delay_damage()
	clif_clearchar_delay()
	guild_agit_break()
	mob_damage()
	npc_event_dequeue()
	pet_lootitem_drop()
	skill_castend_delay()

・トラップ系スキルの修正（skill.c）
	-> アローシャワーで罠全般を吹き飛ばせます
	-> 敵がアンクルに捕捉されているときは飛びません
	　 またこのときブリッツビートでダメージが発生します（自動鷹のときはダメージ分散）
	　 ダメージ通せるスキルが他にもあった気がするけど記憶曖昧なので除外
	-> 罠の耐久HPは3500でそれ以上ダメージが蓄積すると消滅します

・@autolootでサーバクラッシュするバグを多分修正？（mob.c）
　ついでに死亡状態なら自動取得できないように変更
	reported by anonym
・パリィが機能してなかった問題を修正（battle.c, status.c）
	reported by G
・リジェクトソードの武器条件判定を修正（battle.c）
・skill.cの処理改善

----------------------------------------
// 2063 by Yor
Fixed: a vender must have a cart and the skill to open shop.
Improved: call of vending_openvending function.
Improved: open a shop (stop walking, check values, etc...)
5 modified files:
	Readme2060
	(src/map/)
		clif.c
		clif.h
		vending.c
		vending.h

----------------------------------------
// 2062 by Aarlex
・fix char_sql_nick2id for mail system in SQL version.

2 modified files:
	Readme2060
	(conf/)
		char.c

----------------------------------------
// 2061 by Yor
Improved: vending list sending (don't check twice the vender's sd).
Improved: protection of guild messages against hackers.
Renamed: message[] of web chat message -> webchat_message[] (some other functions use message[] in clif.c)
Added: MAX_VENDING macro.
Fixed: Purchase in vending (against hackers).
Moved: text of message aboutvender in msg_athena.conf.
7 modified files:
	Readme2060
	(conf/)
		msg_athena.conf
	(src/map/)
		clif.c
		clif.h
		map.h
		vending.c
		vending.h

----------------------------------------
//2060 by 逆毛鰻

・サーバースナップショット
・version.hの更新
	(src/common)
		version.h		- mod version 2060

//2059以前の変更点はReadmeを参照してください
----------------------------------------
    Athena Dev. v2.1.1       Released: Middle July, 2003
    (c) 2003 Athena Project.
     http://project-yare.de/

1. Athena(アテナ)について
2. このリリースについて
3. 必要な物
4. 使い方
5. 現在の仕様
6. 祝辞
7. 免責事項
8. 募集
9. English


1. アテナについて
    アテナとは2003年1月半ばにでた0052.lzhをベースとして作られているエミュレータの一つです。
    基本的なライセンスはオリジナルがGPLの下に配布されている為、
    これに従いGPLの下配布を許可します。
    /*
        改良版を配布する場合は必ずこのREADMEを書き換えてください。
        何処を改良したのか報告(athena@project-yare.deまで)して貰えると助かります。
        バイナリのみの配布はGPL違反ですので"必ず"ソースも添付してください。
     */
    動作の確認は以下の通りのみ行っています。
    // ただし完璧に動く事を保証するものでありません
    対象CPU: Intel Pentium系   // PentiumII以上で確認.
        FreeBSD 4.8R, 4.6.2R
        Linux RedHat 7.3
        cygwin + gcc 3.2 20020927 (prerelease)
    開発元URL: http://project-yare.de/


2. このリリースについて
    今回のリリースは前回(V2.1)同様開発版のリリースのみです。
    2.1に比べ下記の点が修正されています。
        mapのデフォルト設定が韓国data.grfのみ正常に動作するようになっていた点
        common/timer.cやmap/script.cの幾つかのバグ

    迅速にUpdateを強く推奨するものではありませんが各自の判断で行って下さい。


3. 必要な物
    data.grf      //sdata.grfは必要に応じて
    account.txt   //存在しない場合athena.shが自動生成します
    conf/*.cnf    //Map用とChar用の二種類あります
    conf/npc*.txt //npc設定用ファイルです。複数のファイルに分けることが可能です。
    db/*.txt      //アイテム、job情報など


4. 使い方
    > tar xvfz athena-d?.?.tar.gz
    > cd athena-d?.?.tar.gz
    > make
    > vi conf/char_athena.cnf       //IP(127.0.0.1)の部分を環境に合わせて変更してください
    > vi conf/map_athena.cnf        //同上、またmap設定などは、このファイルで行います。
    > ./athena.sh
    上記を行えば"たぶん"起動します。

    補足:
    conf/npc_sampleJ.txtにはスクリプトの書き方について色々な説明が記載されています。
    もし、独自のMap設定を行ってみたい人や、スクリプトを弄りたい方は参考にしてください。
    ただし、開発中のためスクリプトの仕様が変更される可能性が高いです。
    command.txtには実装済みの特殊コマンドについての説明を記載しています。


5. 現在の仕様
    本鯖と比べておかしい(例えばプバが歩く、ポリンがアイテムを拾わないなど)点は、
    全て現在開発中に因るものです。
    現状としてキャラクタ系及びモンスター系のバグ報告は無視される可能性が高いです。

    バグ報告について必ず発生条件をお書き下さい。
    下にある報告用テンプレートを使って報告して頂くと助かります。
    報告先はエミュ板の開発スレにでも。
    ---- Athena v 2.0 (stable or develop) ----
    【gcc ver】gcc -vを実行時に表示される内容
    【動作システム】FreeBSD, Linux(ディストリビュージョンも), cygwinなど
    【発生内容】mapが落ちてしまった時の表示されていたデバッグ情報など具体的に書いてください。
    【操作内容】具体的にどんな操作を行ったかを書いてください。
    ------------------ END -------------------
    理想はテンプレに加えてmap.coreなどcoreファイルをUploaderにアップして頂くことですが
    問題のMapだけの状態にしcoreの吐く容量に注意してください。
    /*
        確認した限りでは324個ほどmapデータを読み込ませると、
         40MB近いcoreファイルを吐き出します @FreeBSD
         cygwinの場合はstackdumpというファイルになるそうです。
        しかし、coreファイルなどをgzip圧縮などすれば大幅に小さくなります。
         大凡30MBのcoreファイルが2.9MBほどになるようです。
        ですので、もしアップロードする場合はgzip圧縮など各自行ってください。
     */

    今回のリリースだけでなくHISTORYを作成すると大量に記述が必要な為省略しています。
    // 多い日だと本当に結構ありますので‥‥。


6. 祝辞
    今回このAthena開発版を出すに当たって感謝したい方々(順番不同)
        Lemming氏 (Project YARE)
        0052氏 (Uploader)
        35氏 (エミュ開発スレ)
        Johan Lindh氏(Author of memwatch)
        YARE forumのNPC情報を作成した方々
        weiss研究会BBSの様々な情報ファイルを作成した方々
        最後に、.coreファイル達


7. 免責事項
    Athena Projectは一切Athenaの動作に関する保証等は行いません。
    つまり、Athenaは無保証です。
    athena@project-yare.deに動作・操作等に関する質問などを送られても一切お答えできません。
    又Athenaを用いたことにより生じた被害・問題等の責任は一切Athena Projectは負いません。


8. 募集
    athenaの開発に参加したい//興味があるという方ご連絡下さい。
    我々は貴方の参加をお待ちしています。
    // 最新版が欲しいだけで何ら協力して頂けないという方はお断りです;-)
    [募集要項: プログラマ(2-3人)]
        年齢: 不問
        性別: 不問
        言語: 日本語が理解可能
        内容: C言語もしくはC++による開発。(特にネットワークやDBの経験が有る方大募集!)
    [募集要項: 翻訳(?人)]
        年齢: 不問
        性別: 不問
        言語: 日本語、英語が理解可能
        内容: 仏蘭西語、独逸語、西班牙語、伊太利亜語、泰(タイ)語、朝鮮語、中国語へ文献、サイトなどの翻訳
    連絡先: athena@project-yare.de 雑務担当まで。


9. English
     This release is just fixed some bugs in timer.c, script.c and map_athena1.conf.


(c) 2003 Athena Project.

