---
title: 共有データ ソース アイテムをセキュリティで保護する | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- shared data sources [Reporting Services]
- data sources [Reporting Services], shared
- security [Reporting Services], data sources
ms.assetid: 7299e498-0a1a-4821-a22a-5199bb773ce0
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: c4177834a90e2852f4079e3b2bf5a1dd85b9cd51
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641435"
---
# <a name="secure-shared-data-source-items"></a><span data-ttu-id="0bbab-102">共有データ ソース アイテムをセキュリティで保護する</span><span class="sxs-lookup"><span data-stu-id="0bbab-102">Secure Shared Data Source Items</span></span>
  <span data-ttu-id="0bbab-103">共有データ ソース アイテムにセキュリティを設定して、そのアイテムへのアクセスを有効または無効にすることができます。</span><span class="sxs-lookup"><span data-stu-id="0bbab-103">You can set security on a shared data source item to enable or disable access to it.</span></span>  
  
 <span data-ttu-id="0bbab-104">共有データ ソースにアクセスするための最低限の権限 (たとえば、 **閲覧者** ロールにより与えられる権限) を持っているユーザーは、レポート自体の表示を承認されていれば、アイテムを使用するレポートの一覧を表示できます。</span><span class="sxs-lookup"><span data-stu-id="0bbab-104">A user who has minimal access to a shared data source (for example, the access granted through the **Browser** role) can view the list of reports that use the item, provided the user is also authorized to view the reports themselves.</span></span>  
  
 <span data-ttu-id="0bbab-105">それ以上の権限 (たとえば、 **コンテンツ マネージャー** ロールにより与えられる権限) を持つユーザーは、共有データ ソースのプロパティを表示および設定できます。</span><span class="sxs-lookup"><span data-stu-id="0bbab-105">A user who has additional access (such as that granted through the **Content Manager** role) can view and set properties for the shared data source.</span></span>  
  
 <span data-ttu-id="0bbab-106">セキュリティを設定するには、共有データ ソースへのアクセス権を与えられたユーザー アカウントまたはグループ アカウントを指定するロールの割り当てを作成します。</span><span class="sxs-lookup"><span data-stu-id="0bbab-106">To set security, you create a role assignment that specifies which user or group account has access to the shared data source.</span></span> <span data-ttu-id="0bbab-107">共有データ ソース アイテムへのアクセス権を持つユーザーは、名前、説明、接続文字列、および資格情報を変更できます。</span><span class="sxs-lookup"><span data-stu-id="0bbab-107">Users who have access to a shared data source item can change its name, description, connection string, or credential information.</span></span>  
  
## <a name="tasks-and-access-to-items"></a><span data-ttu-id="0bbab-108">タスクおよびアイテムへのアクセス</span><span class="sxs-lookup"><span data-stu-id="0bbab-108">Tasks and Access to Items</span></span>  
 <span data-ttu-id="0bbab-109">ロールの割り当てを作成するときに、以下のタスクを持つロールを使用して、ユーザーとグループに適切な権限を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="0bbab-109">When creating role assignments, use a role that has these tasks to assign appropriate permissions to users and groups.</span></span>  
  
|<span data-ttu-id="0bbab-110">使用するタスク</span><span class="sxs-lookup"><span data-stu-id="0bbab-110">Select this task</span></span>|<span data-ttu-id="0bbab-111">ユーザーに権限を与える操作</span><span class="sxs-lookup"><span data-stu-id="0bbab-111">To give users permission to</span></span>|  
|----------------------|---------------------------------|  
|<span data-ttu-id="0bbab-112">データ ソースの表示</span><span class="sxs-lookup"><span data-stu-id="0bbab-112">View data sources</span></span>|<span data-ttu-id="0bbab-113">フォルダー階層内の共有データ ソース アイテムを表示します。</span><span class="sxs-lookup"><span data-stu-id="0bbab-113">View the shared data source item in the folder hierarchy.</span></span> <span data-ttu-id="0bbab-114">このタスクがないと、アイテムがユーザーに表示されず、利用可能なデータ ソースをユーザーが認識できなくなる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="0bbab-114">Without this task, the item is not visible to users and they may not be aware that the data source is available.</span></span>|  
|<span data-ttu-id="0bbab-115">データ ソースを管理する</span><span class="sxs-lookup"><span data-stu-id="0bbab-115">Manage data sources</span></span>|<span data-ttu-id="0bbab-116">名前、説明、および接続情報を表すプロパティを表示します。</span><span class="sxs-lookup"><span data-stu-id="0bbab-116">View properties that specify the name, description, and connection information.</span></span> <span data-ttu-id="0bbab-117">このタスクは、フォルダー階層内の共有データ ソース アイテムの表示にも使用します。</span><span class="sxs-lookup"><span data-stu-id="0bbab-117">This task is also used to display a shared data source item in the folder hierarchy.</span></span> <span data-ttu-id="0bbab-118">このタスクを選択した場合は、"データ ソースの表示" タスクを省略できます。</span><span class="sxs-lookup"><span data-stu-id="0bbab-118">If you choose this task, you can omit the "View data sources" task.</span></span>|  
|<span data-ttu-id="0bbab-119">アイテムへのセキュリティの設定</span><span class="sxs-lookup"><span data-stu-id="0bbab-119">Set security on items</span></span>|<span data-ttu-id="0bbab-120">共有データ ソースへのアクセスを制御するロールの割り当てを作成および変更します。</span><span class="sxs-lookup"><span data-stu-id="0bbab-120">Create and modify role assignments that control access to the shared data source.</span></span> <span data-ttu-id="0bbab-121">このタスクは、"データ ソースの表示" タスク、または "データ ソースの管理" タスクのいずれかと併用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0bbab-121">This task must be used with either "View data source" or "Manage data sources" tasks.</span></span> <span data-ttu-id="0bbab-122">それ以外の場合、ユーザーはアイテムを選択できないので効果がありません。</span><span class="sxs-lookup"><span data-stu-id="0bbab-122">If it is not, it has no effect because the user cannot select the item.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0bbab-123">参照</span><span class="sxs-lookup"><span data-stu-id="0bbab-123">See Also</span></span>  
 <span data-ttu-id="0bbab-124">[レポート データ ソースを管理する](../report-data/manage-report-data-sources.md) </span><span class="sxs-lookup"><span data-stu-id="0bbab-124">[Manage Report Data Sources](../report-data/manage-report-data-sources.md) </span></span>  
 <span data-ttu-id="0bbab-125">[フォルダーをセキュリティで保護する](secure-folders.md) </span><span class="sxs-lookup"><span data-stu-id="0bbab-125">[Secure Folders](secure-folders.md) </span></span>  
 <span data-ttu-id="0bbab-126">[レポートとリソースの保護](secure-reports-and-resources.md) </span><span class="sxs-lookup"><span data-stu-id="0bbab-126">[Secure Reports and Resources](secure-reports-and-resources.md) </span></span>  
 <span data-ttu-id="0bbab-127">[ネイティブ モードのレポート サーバーに対する権限の許可](granting-permissions-on-a-native-mode-report-server.md) </span><span class="sxs-lookup"><span data-stu-id="0bbab-127">[Granting Permissions on a Native Mode Report Server](granting-permissions-on-a-native-mode-report-server.md) </span></span>  
 [<span data-ttu-id="0bbab-128">Reporting Services データ ソースに資格情報を保存する</span><span class="sxs-lookup"><span data-stu-id="0bbab-128">Store Credentials in a Reporting Services Data Source</span></span>](../report-data/store-credentials-in-a-reporting-services-data-source.md)  
  
  
