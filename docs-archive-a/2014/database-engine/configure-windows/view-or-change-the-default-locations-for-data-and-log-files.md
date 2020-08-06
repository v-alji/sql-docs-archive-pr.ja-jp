---
title: データファイルとログファイルの既定の場所を表示または変更する (SQL Server Management Studio) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- log files [SQL Server], changing default location
- data files [SQL Server], changing default location
ms.assetid: 70a57fda-fcfe-490f-9cf6-5df620e32b2a
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: def6be137aecbab7f2730fa4c2bf210b374a3a7a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87713469"
---
# <a name="view-or-change-the-default-locations-for-data-and-log-files-sql-server-management-studio"></a><span data-ttu-id="136f4-102">データ ファイルとログ ファイルの既定の場所の表示または変更 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="136f4-102">View or Change the Default Locations for Data and Log Files (SQL Server Management Studio)</span></span>
  <span data-ttu-id="136f4-103">このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] で [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]を使用して、新しいデータ ファイルとログ ファイルの既定の場所を表示および変更する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="136f4-103">This topic describes how to view and change the default locations of new data and log files in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="136f4-104">既定のパスはレジストリから取得されます。</span><span class="sxs-lookup"><span data-stu-id="136f4-104">The default path is obtained from the registry.</span></span> <span data-ttu-id="136f4-105">場所を変更した後は、別の場所が指定されない限り、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスで作成されるすべての新しいデータベースに関して、この場所が使用されます。</span><span class="sxs-lookup"><span data-stu-id="136f4-105">After you change the location all new databases created in the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] will use that location if a different location is not specified.</span></span>  
  
 <span data-ttu-id="136f4-106">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="136f4-106">**In This Topic**</span></span>  
  
-   <span data-ttu-id="136f4-107">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="136f4-107">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="136f4-108">Recommendations (推奨事項)</span><span class="sxs-lookup"><span data-stu-id="136f4-108">Recommendations</span></span>](#Recommendations)  
  
-   <span data-ttu-id="136f4-109">**以下を使用してデータ ファイルとログ ファイルの既定の場所を表示または変更するには:**</span><span class="sxs-lookup"><span data-stu-id="136f4-109">**To view or change the data and log file default locations, using:**</span></span>  
  
     [<span data-ttu-id="136f4-110">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="136f4-110">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
-   <span data-ttu-id="136f4-111">**補足情報:**  [既定の場所の変更した後](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="136f4-111">**Follow Up:**  [Changing the Default Locations](#FollowUp)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="136f4-112">はじめに</span><span class="sxs-lookup"><span data-stu-id="136f4-112">Before You Begin</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="136f4-113">推奨事項</span><span class="sxs-lookup"><span data-stu-id="136f4-113">Recommendations</span></span>  
 <span data-ttu-id="136f4-114">データ ファイルとログ ファイルを保護するために、それらがアクセス制御リスト (ACL) によって保護されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="136f4-114">The best practice for protecting your data files and log files is to ensure that they are protected by access control lists (ACLs).</span></span> <span data-ttu-id="136f4-115">ACL は、ファイルを作成するディレクトリのルートに設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="136f4-115">The ACLs should be set on the directory root under which the files are created.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="136f4-116">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="136f4-116">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="136f4-117">Permissions</span><span class="sxs-lookup"><span data-stu-id="136f4-117">Permissions</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="136f4-118">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="136f4-118">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-view-or-change-the-default-locations-for-database-files"></a><span data-ttu-id="136f4-119">データベース ファイルの既定の場所を表示または変更するには</span><span class="sxs-lookup"><span data-stu-id="136f4-119">To view or change the default locations for database files</span></span>  
  
1.  <span data-ttu-id="136f4-120">オブジェクト エクスプローラーで、サーバーを右クリックして **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="136f4-120">In Object Explorer, right-click a server and click **Properties**.</span></span>  
  
2.  <span data-ttu-id="136f4-121">左側のパネルで、 **[データベースの設定]** ページをクリックします。</span><span class="sxs-lookup"><span data-stu-id="136f4-121">In the left panel, click the **Database settings** page.</span></span>  
  
3.  <span data-ttu-id="136f4-122">**[データベースの既定の場所]** パネルに、新しいデータ ファイルと新しいログ ファイルの現在の既定の場所が表示されます。</span><span class="sxs-lookup"><span data-stu-id="136f4-122">In **Database default locations**, view the current default locations for new data files and new log files.</span></span> <span data-ttu-id="136f4-123">既定の場所を変更するには、 **[データ]** フィールドまたは **[ログ]** フィールドに新しい既定のパス名を入力するか、参照ボタンをクリックしてパス名を選択します。</span><span class="sxs-lookup"><span data-stu-id="136f4-123">To change a default location, enter a new default pathname in the **Data** or **Log** field, or click the browse button to find and select a pathname.</span></span>  
  
##  <a name="follow-up-after-changing-the-default-locations"></a><a name="FollowUp"></a><span data-ttu-id="136f4-124">補足情報: 既定の場所を変更した後</span><span class="sxs-lookup"><span data-stu-id="136f4-124">Follow Up: After Changing the Default Locations</span></span>  
 <span data-ttu-id="136f4-125">変更を完了するには、SQLServer サービスをいったん停止してから再起動する必要があります。</span><span class="sxs-lookup"><span data-stu-id="136f4-125">You must stop and start the SQL Server service to complete the change.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="136f4-126">参照</span><span class="sxs-lookup"><span data-stu-id="136f4-126">See Also</span></span>  
 <span data-ttu-id="136f4-127">[CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="136f4-127">[CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql) </span></span>  
 [<span data-ttu-id="136f4-128">データベースの作成</span><span class="sxs-lookup"><span data-stu-id="136f4-128">Create a Database</span></span>](../../relational-databases/databases/create-a-database.md)  
  
  
