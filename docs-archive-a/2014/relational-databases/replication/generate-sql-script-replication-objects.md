---
title: '[SQL スクリプトの生成] (レプリケーション オブジェクト) | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.generatesqlscript.f1
helpviewer_keywords:
- Generate SQL Script dialog box
ms.assetid: b7ccc34e-1c22-44b8-8eb5-f6423af3164e
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 31a4b318eb3a4c0e5d9f79f43efdcf97c42957f9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632345"
---
# <a name="generate-sql-script-replication-objects"></a><span data-ttu-id="53cd2-102">[SQL スクリプトの生成] (レプリケーション オブジェクト)</span><span class="sxs-lookup"><span data-stu-id="53cd2-102">Generate SQL Script (Replication Objects)</span></span>
  <span data-ttu-id="53cd2-103">レプリケーション スクリプトには、パブリケーションやサブスクリプションなど、スクリプト化されたレプリケーション コンポーネントを実装するために必要な [!INCLUDE[tsql](../../includes/tsql-md.md)] システム ストアド プロシージャが含まれます。</span><span class="sxs-lookup"><span data-stu-id="53cd2-103">A replication script contains the [!INCLUDE[tsql](../../includes/tsql-md.md)] system stored procedures necessary to implement the replication components scripted, such as a publication or subscription.</span></span> <span data-ttu-id="53cd2-104">トポロジ内のすべてのレプリケーション コンポーンネントは、ディザスター リカバリー計画の一部としてスクリプト化され、スクリプトはタスクの繰り返しの自動化にも使用することができます。</span><span class="sxs-lookup"><span data-stu-id="53cd2-104">All replication components in a topology should be scripted as part of a disaster recovery plan, and scripts can also be used to automate repetitive tasks.</span></span> <span data-ttu-id="53cd2-105">レプリケーションでは、レプリケーション オブジェクトをスクリプト化するための次の 2 つのダイアログ ボックスが用意されています。</span><span class="sxs-lookup"><span data-stu-id="53cd2-105">Replication offers two dialog boxes for scripting replication objects:</span></span>  
  
-   <span data-ttu-id="53cd2-106">**[SQL スクリプトの生成]** ダイアログ ボックスは、**msCoName** の [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] フォルダーと、すべてのサブ フォルダーのショートカット メニューから利用可能です。</span><span class="sxs-lookup"><span data-stu-id="53cd2-106">**Generate SQL Script**, which is available from the context menu of the **Replication** folder and all subfolders in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="53cd2-107">このダイアログ ボックスを使用して、[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンス上のすべてのレプリケーション オブジェクトのスクリプトを作成できます。</span><span class="sxs-lookup"><span data-stu-id="53cd2-107">This dialog box allows you to script all replication objects on an instance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="53cd2-108">**[SQL スクリプトの生成 \<ObjectName>]** ダイアログ ボックスは、パブリケーションおよびサブスクリプションのショートカット メニューから利用可能です。</span><span class="sxs-lookup"><span data-stu-id="53cd2-108">**Generate SQL Script \<ObjectName>**, which is available from the context menu for publications and subscriptions.</span></span> <span data-ttu-id="53cd2-109">このダイアログ ボックスを使用して、個々のオブジェクトのスクリプトを作成できます。</span><span class="sxs-lookup"><span data-stu-id="53cd2-109">This dialog box allows you to script individual objects.</span></span>  
  
 <span data-ttu-id="53cd2-110">これらのダイアログ ボックスでは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の単一のインスタンスにオブジェクトのスクリプトを作成します。ダイアログ ボックスは、他のインスタンスに接続して関連するオブジェクトのスクリプトを作成することはありません。</span><span class="sxs-lookup"><span data-stu-id="53cd2-110">These dialog boxes script objects on a single instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]; they do not connect to other instances to script related objects.</span></span>  
  
## <a name="generate-sql-script-options"></a><span data-ttu-id="53cd2-111">[SQL スクリプトの生成] ダイアログ ボックスのオプション</span><span class="sxs-lookup"><span data-stu-id="53cd2-111">Generate SQL Script Options</span></span>  
 <span data-ttu-id="53cd2-112">**[ディストリビューターのプロパティ]**</span><span class="sxs-lookup"><span data-stu-id="53cd2-112">**Distributor properties**</span></span>  
 <span data-ttu-id="53cd2-113">ディストリビューターの有効化または無効化、ディストリビューターに関連付けられたパブリッシャーの追加または削除、およびディストリビューション データベースの作成または削除を行うため、ストアド プロシージャのスクリプトを作成します。</span><span class="sxs-lookup"><span data-stu-id="53cd2-113">Select to script stored procedures to: enable or disable the Distributor; add or drop Publishers associated with the Distributor; and create or drop the distribution database.</span></span>  
  
 <span data-ttu-id="53cd2-114">**[次のデータ ソースのパブリケーション]**</span><span class="sxs-lookup"><span data-stu-id="53cd2-114">**Publications in the following data sources**</span></span>  
 <span data-ttu-id="53cd2-115">パブリッシュの有効化または無効化と、パブリケーション、アーティクル、プッシュ サブスクリプション、およびレプリケーション ジョブの作成または削除を行うため、ストアド プロシージャのスクリプトを作成します。</span><span class="sxs-lookup"><span data-stu-id="53cd2-115">Select to script stored procedures to: enable or disable publishing; and create or drop publications, articles, push subscriptions, and replication jobs.</span></span>  
  
 <span data-ttu-id="53cd2-116">**[次のデータ ソース内のサブスクリプション]**</span><span class="sxs-lookup"><span data-stu-id="53cd2-116">**Subscriptions in the following data sources**</span></span>  
 <span data-ttu-id="53cd2-117">プル サブスクリプションとレプリケーション ジョブの作成または削除を行うため、ストアド プロシージャのスクリプトを作成します。</span><span class="sxs-lookup"><span data-stu-id="53cd2-117">Select to script stored procedures to create or drop pull subscriptions and replication jobs.</span></span>  
  
 <span data-ttu-id="53cd2-118">**[コンポーネントを作成または有効にする]** と **[コンポーネントを削除または無効にする]**</span><span class="sxs-lookup"><span data-stu-id="53cd2-118">**To create or enable the components** and **To drop or disable the components**</span></span>  
 <span data-ttu-id="53cd2-119">スクリプトにレプリケーション オブジェクトの作成または削除を行うコマンドを含めるかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="53cd2-119">Specify whether the script should include commands for creating or dropping a replication object.</span></span> [!INCLUDE[msCoName](../../includes/msconame-md.md)] <span data-ttu-id="53cd2-120">では、コンポーネントの有効化と無効化を行うために、ダイアログ ボックスを使用してスクリプト セットを作成することを推奨します。</span><span class="sxs-lookup"><span data-stu-id="53cd2-120">recommends that you use the dialog box to create a set of scripts for enabling and disabling components.</span></span>  
  
 <span data-ttu-id="53cd2-121">**[レプリケーション ジョブ]**</span><span class="sxs-lookup"><span data-stu-id="53cd2-121">**Replication jobs**</span></span>  
 <span data-ttu-id="53cd2-122">ストアド プロシージャの呼び出しに加えて、レプリケーション ジョブのスクリプトを作成します。</span><span class="sxs-lookup"><span data-stu-id="53cd2-122">Select to script replication jobs in addition to stored procedure calls.</span></span> <span data-ttu-id="53cd2-123">このオプションは、ディストリビューターからスクリプトを作成する場合にのみ利用可能です。</span><span class="sxs-lookup"><span data-stu-id="53cd2-123">This option is available only when scripting from a Distributor.</span></span>  
  
 <span data-ttu-id="53cd2-124">レプリケーション ストアド プロシージャは実行時に必要なジョブを作成します。そのため、このオプションを選択する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="53cd2-124">Replication stored procedures create the necessary jobs when they are executed, so it is not required to select this option.</span></span> <span data-ttu-id="53cd2-125">ただし、作成したジョブを記録しておくと、個々のジョブを再作成する必要が生じた場合に役に立ちます。</span><span class="sxs-lookup"><span data-stu-id="53cd2-125">However, it can be useful to have a record of the jobs created in case an individual job must be recreated.</span></span>  
  
## <a name="generate-sql-script-objectname-options"></a><span data-ttu-id="53cd2-126">[SQL スクリプトの生成 \<ObjectName>] ダイアログ ボックスのオプション</span><span class="sxs-lookup"><span data-stu-id="53cd2-126">Generate SQL Script \<ObjectName> Options</span></span>  
 <span data-ttu-id="53cd2-127">**[コンポーネントを作成または有効にする]** と **[コンポーネントを削除または無効にする]**</span><span class="sxs-lookup"><span data-stu-id="53cd2-127">**To create or enable the components** and **To drop or disable the components**</span></span>  
 <span data-ttu-id="53cd2-128">スクリプトにレプリケーション オブジェクトの作成または削除を行うコマンドを含めるかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="53cd2-128">Specify whether the script should include commands for creating or dropping a replication object.</span></span> [!INCLUDE[msCoName](../../includes/msconame-md.md)] <span data-ttu-id="53cd2-129">では、コンポーネントの有効化と無効化を行うために、ダイアログ ボックスを使用してスクリプト セットを作成することを推奨します。</span><span class="sxs-lookup"><span data-stu-id="53cd2-129">recommends that you use the dialog box, creating a set of scripts for enabling and disabling components.</span></span>  
  
 <span data-ttu-id="53cd2-130">**[レプリケーション ジョブ]**</span><span class="sxs-lookup"><span data-stu-id="53cd2-130">**Replication jobs**</span></span>  
 <span data-ttu-id="53cd2-131">このオプションは、 **[SQL スクリプトの生成]** ダイアログ ボックスからのみ利用可能です。</span><span class="sxs-lookup"><span data-stu-id="53cd2-131">This option is available only from the **Generate SQL Script** dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53cd2-132">参照</span><span class="sxs-lookup"><span data-stu-id="53cd2-132">See Also</span></span>  
 [<span data-ttu-id="53cd2-133">レプリケーションのスクリプト作成</span><span class="sxs-lookup"><span data-stu-id="53cd2-133">Scripting Replication</span></span>](scripting-replication.md)  
  
  
