---
title: 可用性セットや可用性ゾーン上の単一 VM インスタンスの可用性について
date: 2024-05-02 12:00:00
tags:
  - Information
  - VM
disableDisclaimer: false
---

こんにちは。Azure テクニカル サポート チームです。 

本ブログ記事では、可用性セットや可用性ゾーン上に単一の VM インスタンスのみを構成した場合の SLA についてご案内いたします。 

<!-- more -->

可用性セットや可用性ゾーンは、VM 群を稼働するハードウェアが単一障害点とならないように分散配置することで基盤障害の影響を一部の VM に限定するサービスとなります。

例えば、あるシステムにおいてゾーン 1 とゾーン 2 に 1 台ずつ VM を構成している場合、ゾーン 1 で基盤障害が発生した際にはゾーン 1 の VM は影響を受けますが、ゾーン 2 の VM は影響を受けずに稼働を継続するため、システム全体としての可用性を向上させることができます。  
すなわち、一つ一つの VM インスタンスとしての可用性には変わりはなく、可用性セットや可用性ゾーンに複数の VM を冗長構成で構築いただくことで、初めて高可用性の恩恵を受けることが可能となります。  
そのため、VM インスタンス 1 台のみを可用性セットや可用性ゾーンに構成することは可能ですが、可用性が向上している訳ではございませんので、SLA の考え方としては可用性セット・可用性ゾーン無しの状態と同じ単一インスタンスとしての計算となります。  

可用性セットや可用性ゾーンを構成した場合の SLA については、構成した全ての VM インスタンスが停止してしまった際にダウンタイムとして計算されるような形となります。  
一つ以上のインスタンスが稼働を継続できている場合にはそれぞれのインスタンスとしての SLA のみが適用されますことご留意ください。

Azure VM の可用性セットおよび可用性ゾーンの詳細については、以下の公式ドキュメントをご確認いただけますと幸いでございます。

■ご参考：Azure Virtual Machines の可用性オプション  
https://learn.microsoft.com/ja-jp/azure/virtual-machines/availability  

また、SLA については毎月最新の情報が公開されますため、詳細につきましては、以下のサイトにございます Word ファイルをダウンロードいただき、ご確認いただきますと幸いです。  
最新バージョンはサイト上部の \[Download\] からご確認いただけますので、”仮想マシン” セクションをご覧ください。  

■ご参考： Service Level Agreements (SLA) for Online Services  
https://www.microsoft.com/licensing/docs/view/Service-Level-Agreements-SLA-for-Online-Services?lang=18  

![](./sla-singlevm-availability/img001.png)

簡単ではございますが、上記の内容がお客様のお役に立ちますと幸いでございます。