---
title: フォルダーをセキュリティで保護する | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- high-security folders [Reporting Services]
- low-security folders
- folders [Reporting Services], security
- security [Reporting Services], folders
ms.assetid: 0fd91f77-0143-476b-9af0-87293be78e44
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 483b3108713032b3aaf566208f39f6c2f705da1a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633719"
---
# <a name="secure-folders"></a><span data-ttu-id="15594-102">フォルダーをセキュリティで保護する</span><span class="sxs-lookup"><span data-stu-id="15594-102">Secure Folders</span></span>
  <span data-ttu-id="15594-103">フォルダーのセキュリティは、レポート サーバーのすべてのコンテンツをセキュリティで保護するための基盤となります。</span><span class="sxs-lookup"><span data-stu-id="15594-103">Folder security is the foundation for securing all content in a report server.</span></span> <span data-ttu-id="15594-104">セキュリティはフォルダー階層全体に継承されるので、フォルダー階層の大きさにかかわらず、特定のアクセス権を許可することができます。</span><span class="sxs-lookup"><span data-stu-id="15594-104">Because security is inherited throughout the folder structure, you can designate large or small sections of the folder hierarchy to allow for certain kinds of access.</span></span>  
  
 <span data-ttu-id="15594-105">高レベルのセキュリティを設定したフォルダーは、機密情報を含むレポートを保存したり、ステージング領域として使用できます。たとえば、レポートを最終運用場所に移動する前にテストするためのフォルダーを作成できます。</span><span class="sxs-lookup"><span data-stu-id="15594-105">High-security folders can be used to store confidential reports or as staging areas; for example, you can have a folder that you use to test reports before moving them to a final location.</span></span> <span data-ttu-id="15594-106">この領域へのアクセスを制御するため、レポート作成者のみがアイテムを追加および削除できるロールの割り当てと、テスターにレポートの実行を許可しアイテムの追加と削除を禁止するロールの割り当てを定義できます。</span><span class="sxs-lookup"><span data-stu-id="15594-106">To control access to this area, you can define one role assignment that allows only report authors to add and delete items, and a second role assignment that allows testers to run reports but not to add or remove items.</span></span> <span data-ttu-id="15594-107">テスターとレポート作成者に対し明示的にロールの割り当てが定義されるため、ローカルのシステム管理者以外のユーザーはこのフォルダーにアクセスできません。</span><span class="sxs-lookup"><span data-stu-id="15594-107">Because the role assignments are defined explicitly for testers and report authors, no other users (except for local system administrators) can access the folder.</span></span>  
  
 <span data-ttu-id="15594-108">セキュリティ レベルの低いフォルダーは、簡単にアクセスできるようにするレポートの格納場所として使用できます。</span><span class="sxs-lookup"><span data-stu-id="15594-108">Low-security folders can be used to store reports that you want to be easily accessible.</span></span>  
  
 <span data-ttu-id="15594-109">アイテムレベルのセキュリティの基盤となっているフォルダーのセキュリティは、レポート サーバーのフォルダー階層のルート ノードである [ホーム] フォルダーを起点とします。</span><span class="sxs-lookup"><span data-stu-id="15594-109">Folder security forms the basis of item-level security, starting with the root node of the report server folder hierarchy, the Home folder.</span></span> <span data-ttu-id="15594-110">セキュリティは継承されるので、[ホーム] フォルダーに設定するセキュリティ ポリシーは厳しく制限することを推奨します。</span><span class="sxs-lookup"><span data-stu-id="15594-110">Because security is inherited, it is advisable to set a fairly restrictive security policy on the Home folder.</span></span> <span data-ttu-id="15594-111">たとえば、[ホーム] フォルダーのロールの割り当てで **Browser** ロールを使用すると、アクセスを表示のみに制限できます。</span><span class="sxs-lookup"><span data-stu-id="15594-111">Using the **Browser** role in Home folder role assignments does exactly that by providing view-only access.</span></span>  
  
## <a name="tasks-and-folder-access"></a><span data-ttu-id="15594-112">タスクとフォルダー アクセス</span><span class="sxs-lookup"><span data-stu-id="15594-112">Tasks and Folder Access</span></span>  
 <span data-ttu-id="15594-113">フォルダーに対してロールの割り当てを作成するときは、次の表のタスクを使用することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="15594-113">When creating role assignments for folders, consider the tasks listed in the following table.</span></span>  
  
|<span data-ttu-id="15594-114">使用するタスク</span><span class="sxs-lookup"><span data-stu-id="15594-114">Select this task</span></span>|<span data-ttu-id="15594-115">与えられる権限</span><span class="sxs-lookup"><span data-stu-id="15594-115">To give permission to</span></span>|  
|----------------------|---------------------------|  
|<span data-ttu-id="15594-116">フォルダーの表示</span><span class="sxs-lookup"><span data-stu-id="15594-116">View folders</span></span>|<span data-ttu-id="15594-117">フォルダー階層と、フォルダーがいつ作成および変更されたかを示す読み取り専用のプロパティを表示できます。</span><span class="sxs-lookup"><span data-stu-id="15594-117">View the folder hierarchy and read-only properties that indicate when the folder was created and modified.</span></span><br /><br /> <span data-ttu-id="15594-118">ユーザーは、"レポートの表示"、"モデルの表示"、"リソースの表示"、"データ ソースの表示" の各タスクが含まれているロールに割り当てられない限り、フォルダーのアイテムを表示できません。</span><span class="sxs-lookup"><span data-stu-id="15594-118">Users cannot view items in the folder unless they are assigned to roles that also include the following tasks: "View reports," "View models", "View resources," and "View data sources."</span></span>|  
|<span data-ttu-id="15594-119">フォルダーの管理</span><span class="sxs-lookup"><span data-stu-id="15594-119">Manage folders</span></span>|<span data-ttu-id="15594-120">フォルダーのプロパティの表示、名前や説明の変更、別の場所への移動を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="15594-120">View folder properties, change the name or description, or move the folder to another location.</span></span> <span data-ttu-id="15594-121">このタスクでは、フォルダーの作成も許可されます。</span><span class="sxs-lookup"><span data-stu-id="15594-121">This task allows users to create folders.</span></span>|  
|<span data-ttu-id="15594-122">レポートの管理</span><span class="sxs-lookup"><span data-stu-id="15594-122">Manage reports</span></span>|<span data-ttu-id="15594-123">ファイル システムからフォルダーにレポートを追加したり、レポート デザイナーからレポート サーバーにレポートをパブリッシュしたりできます。</span><span class="sxs-lookup"><span data-stu-id="15594-123">Add reports from the file system to a folder and publish reports from Report Designer to the report server.</span></span>|  
|<span data-ttu-id="15594-124">データ ソースを管理する</span><span class="sxs-lookup"><span data-stu-id="15594-124">Manage data sources</span></span>|<span data-ttu-id="15594-125">新しい共有データ ソース アイテムをフォルダーに追加したり、既存の共有データ ソースを変更したりできます。</span><span class="sxs-lookup"><span data-stu-id="15594-125">Add new shared data source items to a folder and change existing shared data sources.</span></span>|  
|<span data-ttu-id="15594-126">アイテムへのセキュリティの設定</span><span class="sxs-lookup"><span data-stu-id="15594-126">Set security on items</span></span>|<span data-ttu-id="15594-127">フォルダーへのアクセスを制御するロールの割り当てを作成および変更できます。</span><span class="sxs-lookup"><span data-stu-id="15594-127">Create and modify role assignments that control access to the folder.</span></span> <span data-ttu-id="15594-128">このタスクは、"フォルダーの表示" または "フォルダーの管理" のいずれかと併用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="15594-128">This task must be used with either "View folders" or "Manage folders."</span></span> <span data-ttu-id="15594-129">それ以外の場合、ユーザーがアイテムを選択できないので効果がありません。</span><span class="sxs-lookup"><span data-stu-id="15594-129">If it is not, it will have no effect because the user will not be able to select the item.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="15594-130">参照</span><span class="sxs-lookup"><span data-stu-id="15594-130">See Also</span></span>  
 <span data-ttu-id="15594-131">[レポートとリソースの保護](secure-reports-and-resources.md) </span><span class="sxs-lookup"><span data-stu-id="15594-131">[Secure Reports and Resources](secure-reports-and-resources.md) </span></span>  
 <span data-ttu-id="15594-132">[共有データ ソース アイテムをセキュリティで保護する](secure-shared-data-source-items.md) </span><span class="sxs-lookup"><span data-stu-id="15594-132">[Secure Shared Data Source Items](secure-shared-data-source-items.md) </span></span>  
 [<span data-ttu-id="15594-133">ネイティブ モードのレポート サーバーに対する権限の許可</span><span class="sxs-lookup"><span data-stu-id="15594-133">Granting Permissions on a Native Mode Report Server</span></span>](granting-permissions-on-a-native-mode-report-server.md)  
  
  
