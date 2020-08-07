---
title: ツールのオプションとレイアウトの設定 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Database Engine [SQL Server], tutorials
ms.assetid: 43e97ce0-97bc-4a27-9485-5bbeb7190b85
author: stevestein
ms.author: sstein
ms.openlocfilehash: 96d853a85b8ee4d451c55d7ea59af3755887be22
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87719215"
---
# <a name="setting-tool-options-and-layout"></a><span data-ttu-id="a3c74-102">ツール オプションとレイアウトの設定</span><span class="sxs-lookup"><span data-stu-id="a3c74-102">Setting Tool Options and Layout</span></span>
  <span data-ttu-id="a3c74-103">起動時に表示するグラフィカル ユーザー インターフェイス (GUI)、使用するフォント、および他のツールの機能を構成するオプションを設定し、データベース エンジン チューニング アドバイザーの使用方法を最適化することができます。</span><span class="sxs-lookup"><span data-stu-id="a3c74-103">You can set options that configure what the Database Engine Tuning Advisor graphical user interface (GUI) displays on startup, the font it uses, and other tool functionality to best support how you use it.</span></span> <span data-ttu-id="a3c74-104">このページの演習では、ユーザーが設定できるオプションとその設定方法について学習します。</span><span class="sxs-lookup"><span data-stu-id="a3c74-104">The practices on this page familiarize you with the options you can set, and how to set them.</span></span>  
  
### <a name="set-the-tool-options"></a><span data-ttu-id="a3c74-105">ツール オプションの設定</span><span class="sxs-lookup"><span data-stu-id="a3c74-105">Set the tool options</span></span>  
  
1.  <span data-ttu-id="a3c74-106">データベース エンジン チューニング アドバイザーを起動します。</span><span class="sxs-lookup"><span data-stu-id="a3c74-106">Start the Database Engine Tuning Advisor.</span></span> <span data-ttu-id="a3c74-107">Windows の **[スタート]** ボタンをクリックし、 **[すべてのプログラム]** をポイントして、[ [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)]] をポイントし、 **[パフォーマンス ツール]** をポイントして、 **[データベース エンジン チューニング アドバイザー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a3c74-107">On the Windows **Start** menu, point to **All Programs**, point to [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)], point to **Performance Tools**, and click **Database Engine Tuning Advisor**.</span></span>  
  
2.  <span data-ttu-id="a3c74-108">**[ツール]** メニューの **[オプション]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a3c74-108">On the **Tools** menu, click **Options**.</span></span>  
  
3.  <span data-ttu-id="a3c74-109">**[オプション]** ダイアログ ボックスが開き、次のオプションが表示されます。</span><span class="sxs-lookup"><span data-stu-id="a3c74-109">In the **Options** dialog box, view the following options:</span></span>  
  
    -   <span data-ttu-id="a3c74-110">**[スタートアップ時]** ボックスの一覧には、データベース エンジン チューニング アドバイザーの起動時に表示されるアイテムが示されます。</span><span class="sxs-lookup"><span data-stu-id="a3c74-110">Expand the **On startup** list to view what Database Engine Tuning Advisor can display when it is started.</span></span> <span data-ttu-id="a3c74-111">既定では、 **[新しいセッションを表示します]** が選択されています。</span><span class="sxs-lookup"><span data-stu-id="a3c74-111">By default, **Show a new session** is selected.</span></span>  
  
    -   <span data-ttu-id="a3c74-112">[**フォントの変更**] をクリックして、[**全般**] タブのデータベースとテーブルの一覧で選択できるフォントを確認します。このオプションで選択したフォントは、チューニングの実行後にデータベースエンジンチューニングアドバイザー推奨設定のグリッドおよびレポートでも使用されます。</span><span class="sxs-lookup"><span data-stu-id="a3c74-112">Click **Change Font** to see what fonts you can choose for the lists of databases and tables on the **General** tab. The fonts you choose for this option also are used in Database Engine Tuning Advisor recommendation grids and reports after you have performed tuning.</span></span> <span data-ttu-id="a3c74-113">既定ではシステム フォントが使用されます。</span><span class="sxs-lookup"><span data-stu-id="a3c74-113">By default, Database Engine Tuning Advisor uses system fonts.</span></span>  
  
    -   <span data-ttu-id="a3c74-114">**[最近使用した項目の一覧に表示する項目数]** には、 **1** ～ **10**の値を設定できます。</span><span class="sxs-lookup"><span data-stu-id="a3c74-114">The **Number of items in most recently used lists** can be set between **1** and **10**.</span></span> <span data-ttu-id="a3c74-115">このオプションでは、 **[ファイル]** メニューの **[最新のセッション]** または **[最近使ったファイル]** をクリックしたときに表示される最大項目数を設定します。</span><span class="sxs-lookup"><span data-stu-id="a3c74-115">This sets the maximum number of items in the lists displayed by clicking **Recent Sessions** or **Recent Files** on the **File** menu.</span></span> <span data-ttu-id="a3c74-116">既定では **4**に設定されています。</span><span class="sxs-lookup"><span data-stu-id="a3c74-116">By default, this option is set to **4**.</span></span>  
  
    -   <span data-ttu-id="a3c74-117">**[最後のチューニング オプションを保存する]** チェック ボックスをオンにした場合、既定では、最後のチューニング セッションで指定したチューニング オプションが次のチューニング セッションで使用されます。</span><span class="sxs-lookup"><span data-stu-id="a3c74-117">When **Remember my last tuning options** is checked, by default Database Engine Tuning Advisor uses the tuning options you specified for your last tuning session for the next tuning session.</span></span> <span data-ttu-id="a3c74-118">データベース エンジン チューニング アドバイザーの既定のチューニング オプションを使用するには、このチェック ボックスをオフにします。</span><span class="sxs-lookup"><span data-stu-id="a3c74-118">Clear this check box to use Database Engine Tuning Advisor tuning option defaults.</span></span> <span data-ttu-id="a3c74-119">既定では、このオプションが選択されています。</span><span class="sxs-lookup"><span data-stu-id="a3c74-119">By default, this option is selected.</span></span>  
  
    -   <span data-ttu-id="a3c74-120">誤ってチューニング セッションを削除しないよう、既定では **[完全にセッションを削除する前に確認する]** がオンになっています。</span><span class="sxs-lookup"><span data-stu-id="a3c74-120">By default, **Ask before permanently deleting sessions** is checked to avoid accidentally deleting tuning sessions.</span></span>  
  
    -   <span data-ttu-id="a3c74-121">データベース エンジン チューニング アドバイザーによるワークロードの分析が完了する前に、間違ってチューニング セッションを停止しないように、既定では **[セッションの分析を停止する前に確認する]** がオンになっています。</span><span class="sxs-lookup"><span data-stu-id="a3c74-121">By default, **Ask before stopping session analysis** is checked to avoid accidentally stopping a tuning session before Database Engine Tuning Advisor has finished analyzing a workload.</span></span>  
  
## <a name="next-lesson"></a><span data-ttu-id="a3c74-122">次のレッスン</span><span class="sxs-lookup"><span data-stu-id="a3c74-122">Next Lesson</span></span>  
 [<span data-ttu-id="a3c74-123">レッスン 2:データベース エンジン チューニング アドバイザーの使用</span><span class="sxs-lookup"><span data-stu-id="a3c74-123">Lesson 2: Using Database Engine Tuning Advisor</span></span>](../../relational-databases/performance/database-engine-tuning-advisor.md)  
  
  
