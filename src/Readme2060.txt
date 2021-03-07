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
�EASPD�̍ő�l��PK,GVG,PVP�Ōʂɐ����ł���悤�ɒǉ�
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
�E�t���A�h���i�������b�V�����������U���ɔ��f����Ă���_���C���B
�E�����͕ϊ���SP_MAX�ł͎g�p�o���Ȃ��悤�ɏC��
�@�i�{�I����X���b�h�S 20 ���j
�@�g�p�ł��Ȃ��󋵂Ŏg�p���s���b�Z�[�W���o��E�o�Ȃ���������Ȃ��̂�
�@�Ƃ肠�����g�p���s���b�Z�[�W���o��悤�ɂ��Ă���܂�
	Readme2060
	(db/)
		skill_require_db.txt
	(src/map/)
		skill.c
		status.c
----------------------------------------
// 2072 by luc
�E�X�L���˒��̌�����
�Epet_db.txt�̌뎚���C��
�ENPC�X�N���v�g�̏C��
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

�E2067��MAX_SKILL�̔��菇���~�X���Ă��̂��C���ipc.c�j
		pointed out by Yor, thx a lot!!
�E2068��battle_config.gvg_flee_penalty�̏����������߂��istatus.c�j
�E�J�[�h���ʂɂ��R�[�}����ё������@�\���ĂȂ������o�O���C���ibattle.c�j

----------------------------------------
//2068 by ARIA

�EMC�̏��������PK,PVP,GVG�ł��ꂼ��battle_athena.conf�Ō��߂��悤�ɒǉ�

----------------------------------------
//2067 by Rayce

�Epc.c, unit.c�̏������P
�Eskill_unit_db.txt�̐�����doc/db_ref.txt�ɋL�q
�Eskill.c��skill_misfire.txt��skill_prohibition_zone.txt�Ɋւ���ǂݍ���
�@�����̃R�����g�A�E�g�𖕏�
�Eclif.c����db.h��include���폜�i2064�̂��c���j
�EGvG�}�b�v�ŃA���e�B�y�C�������g���g�p�s�ɂ��鏈����pc.c����؂藣����
�@db/item_prohibition_zone.txt�Ő��䂷��悤�ɕύX
�E�N���[���X�L���̔�����_���[�W�����O�Ɉړ�
	battle_skill_attack()

----------------------------------------
//2066 by luc
�E�G���[ E2313 clif.c 5778: �萔�����K�v(�֐� clif_showvendingboard )
�E�G���[ E2313 clif.c 5801: �萔�����K�v(�֐� clif_closevendingboard )
�R���p�C�����ɏ�L�̃G���[���o�邽�߁Aclif.c�̈ꕔ�̊����߂��B
----------------------------------------
//2065 by luc
�ENPC�X�N���v�g�̏C��
	(npc/town)
		npc_town_alberta.txt
		npc_town_guide.txt
	(npc/quest)
		npc_event_dye.txt
	thanks to AthenaDev

----------------------------------------
//2064 by Rayce

�Eadd_timer() �ɋN�����郁�������[�N�΍�Ƃ���add_timer2() ��ǉ��itimer.*�j
�@�T�[�o�v���O�����I�����Ƀ^�C�}�[�ҋ@���̃f�[�^��timer.c������free���܂�
	battle_delay_damage()
	clif_clearchar_delay()
	guild_agit_break()
	mob_damage()
	npc_event_dequeue()
	pet_lootitem_drop()
	skill_castend_delay()

�E�g���b�v�n�X�L���̏C���iskill.c�j
	-> �A���[�V�����[��㩑S�ʂ𐁂���΂��܂�
	-> �G���A���N���ɕߑ�����Ă���Ƃ��͔�т܂���
	�@ �܂����̂Ƃ��u���b�c�r�[�g�Ń_���[�W���������܂��i������̂Ƃ��̓_���[�W���U�j
	�@ �_���[�W�ʂ���X�L�������ɂ��������C�����邯�ǋL���B���Ȃ̂ŏ��O
	-> 㩂̑ϋvHP��3500�ł���ȏ�_���[�W���~�ς���Ə��ł��܂�

�E@autoloot�ŃT�[�o�N���b�V������o�O�𑽕��C���H�imob.c�j
�@���łɎ��S��ԂȂ玩���擾�ł��Ȃ��悤�ɕύX
	reported by anonym
�E�p���B���@�\���ĂȂ����������C���ibattle.c, status.c�j
	reported by G
�E���W�F�N�g�\�[�h�̕������������C���ibattle.c�j
�Eskill.c�̏������P

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
�Efix char_sql_nick2id for mail system in SQL version.

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
//2060 by �t�щV

�E�T�[�o�[�X�i�b�v�V���b�g
�Eversion.h�̍X�V
	(src/common)
		version.h		- mod version 2060

//2059�ȑO�̕ύX�_��Readme���Q�Ƃ��Ă�������
----------------------------------------
    Athena Dev. v2.1.1       Released: Middle July, 2003
    (c) 2003 Athena Project.
     http://project-yare.de/

1. Athena(�A�e�i)�ɂ���
2. ���̃����[�X�ɂ���
3. �K�v�ȕ�
4. �g����
5. ���݂̎d�l
6. �j��
7. �Ɛӎ���
8. ��W
9. English


1. �A�e�i�ɂ���
    �A�e�i�Ƃ�2003�N1�����΂ɂł�0052.lzh���x�[�X�Ƃ��č���Ă���G�~�����[�^�̈�ł��B
    ��{�I�ȃ��C�Z���X�̓I���W�i����GPL�̉��ɔz�z����Ă���ׁA
    ����ɏ]��GPL�̉��z�z�������܂��B
    /*
        ���ǔł�z�z����ꍇ�͕K������README�����������Ă��������B
        ���������ǂ����̂���(athena@project-yare.de�܂�)���ĖႦ��Ə�����܂��B
        �o�C�i���݂̂̔z�z��GPL�ᔽ�ł��̂�"�K��"�\�[�X���Y�t���Ă��������B
     */
    ����̊m�F�͈ȉ��̒ʂ�̂ݍs���Ă��܂��B
    // �����������ɓ�������ۏ؂�����̂ł���܂���
    �Ώ�CPU: Intel Pentium�n   // PentiumII�ȏ�Ŋm�F.
        FreeBSD 4.8R, 4.6.2R
        Linux RedHat 7.3
        cygwin + gcc 3.2 20020927 (prerelease)
    �J����URL: http://project-yare.de/


2. ���̃����[�X�ɂ���
    ����̃����[�X�͑O��(V2.1)���l�J���ł̃����[�X�݂̂ł��B
    2.1�ɔ�׉��L�̓_���C������Ă��܂��B
        map�̃f�t�H���g�ݒ肪�؍�data.grf�̂ݐ���ɓ��삷��悤�ɂȂ��Ă����_
        common/timer.c��map/script.c�̊���̃o�O

    �v����Update����������������̂ł͂���܂��񂪊e���̔��f�ōs���ĉ������B


3. �K�v�ȕ�
    data.grf      //sdata.grf�͕K�v�ɉ�����
    account.txt   //���݂��Ȃ��ꍇathena.sh�������������܂�
    conf/*.cnf    //Map�p��Char�p�̓��ނ���܂�
    conf/npc*.txt //npc�ݒ�p�t�@�C���ł��B�����̃t�@�C���ɕ����邱�Ƃ��\�ł��B
    db/*.txt      //�A�C�e���Ajob���Ȃ�


4. �g����
    > tar xvfz athena-d?.?.tar.gz
    > cd athena-d?.?.tar.gz
    > make
    > vi conf/char_athena.cnf       //IP(127.0.0.1)�̕��������ɍ��킹�ĕύX���Ă�������
    > vi conf/map_athena.cnf        //����A�܂�map�ݒ�Ȃǂ́A���̃t�@�C���ōs���܂��B
    > ./athena.sh
    ��L���s����"���Ԃ�"�N�����܂��B

    �⑫:
    conf/npc_sampleJ.txt�ɂ̓X�N���v�g�̏������ɂ��ĐF�X�Ȑ������L�ڂ���Ă��܂��B
    �����A�Ǝ���Map�ݒ���s���Ă݂����l��A�X�N���v�g��M�肽�����͎Q�l�ɂ��Ă��������B
    �������A�J�����̂��߃X�N���v�g�̎d�l���ύX�����\���������ł��B
    command.txt�ɂ͎����ς݂̓���R�}���h�ɂ��Ă̐������L�ڂ��Ă��܂��B


5. ���݂̎d�l
    �{�I�Ɣ�ׂĂ�������(�Ⴆ�΃v�o�������A�|�������A�C�e�����E��Ȃ��Ȃ�)�_�́A
    �S�Č��݊J�����Ɉ�����̂ł��B
    ����Ƃ��ăL�����N�^�n�y�у����X�^�[�n�̃o�O�񍐂͖��������\���������ł��B

    �o�O�񍐂ɂ��ĕK�������������������������B
    ���ɂ���񍐗p�e���v���[�g���g���ĕ񍐂��Ē����Ə�����܂��B
    �񍐐�̓G�~���̊J���X���ɂł��B
    ---- Athena v 2.0 (stable or develop) ----
    �ygcc ver�zgcc -v�����s���ɕ\���������e
    �y����V�X�e���zFreeBSD, Linux(�f�B�X�g���r���[�W������), cygwin�Ȃ�
    �y�������e�zmap�������Ă��܂������̕\������Ă����f�o�b�O���Ȃǋ�̓I�ɏ����Ă��������B
    �y������e�z��̓I�ɂǂ�ȑ�����s�������������Ă��������B
    ------------------ END -------------------
    ���z�̓e���v���ɉ�����map.core�Ȃ�core�t�@�C����Uploader�ɃA�b�v���Ē������Ƃł���
    ����Map�����̏�Ԃɂ�core�̓f���e�ʂɒ��ӂ��Ă��������B
    /*
        �m�F��������ł�324�ق�map�f�[�^��ǂݍ��܂���ƁA
         40MB�߂�core�t�@�C����f���o���܂� @FreeBSD
         cygwin�̏ꍇ��stackdump�Ƃ����t�@�C���ɂȂ邻���ł��B
        �������Acore�t�@�C���Ȃǂ�gzip���k�Ȃǂ���Α啝�ɏ������Ȃ�܂��B
         ��}30MB��core�t�@�C����2.9MB�قǂɂȂ�悤�ł��B
        �ł��̂ŁA�����A�b�v���[�h����ꍇ��gzip���k�ȂǊe���s���Ă��������B
     */

    ����̃����[�X�����łȂ�HISTORY���쐬����Ƒ�ʂɋL�q���K�v�Ȉ׏ȗ����Ă��܂��B
    // ���������Ɩ{���Ɍ��\����܂��̂Łd�d�B


6. �j��
    ���񂱂�Athena�J���ł��o���ɓ������Ċ��ӂ��������X(���ԕs��)
        Lemming�� (Project YARE)
        0052�� (Uploader)
        35�� (�G�~���J���X��)
        Johan Lindh��(Author of memwatch)
        YARE forum��NPC�����쐬�������X
        weiss������BBS�̗l�X�ȏ��t�@�C�����쐬�������X
        �Ō�ɁA.core�t�@�C���B


7. �Ɛӎ���
    Athena Project�͈��Athena�̓���Ɋւ���ۏؓ��͍s���܂���B
    �܂�AAthena�͖��ۏ؂ł��B
    athena@project-yare.de�ɓ���E���쓙�Ɋւ��鎿��Ȃǂ𑗂��Ă���؂������ł��܂���B
    ��Athena��p�������Ƃɂ�萶������Q�E��蓙�̐ӔC�͈��Athena Project�͕����܂���B


8. ��W
    athena�̊J���ɎQ��������//����������Ƃ��������A���������B
    ��X�͋M���̎Q�������҂����Ă��܂��B
    // �ŐV�ł��~���������ŉ��狦�͂��Ē����Ȃ��Ƃ������͂��f��ł�;-)
    [��W�v��: �v���O���}(2-3�l)]
        �N��: �s��
        ����: �s��
        ����: ���{�ꂪ�����\
        ���e: C�����������C++�ɂ��J���B(���Ƀl�b�g���[�N��DB�̌o�����L������W!)
    [��W�v��: �|��(?�l)]
        �N��: �s��
        ����: �s��
        ����: ���{��A�p�ꂪ�����\
        ���e: ��������A�ƈ��A���ǉ��A�ɑ�������A��(�^�C)��A���N��A������֕����A�T�C�g�Ȃǂ̖|��
    �A����: athena@project-yare.de �G���S���܂ŁB


9. English
     This release is just fixed some bugs in timer.c, script.c and map_athena1.conf.


(c) 2003 Athena Project.

