---
title: 個人用レポートをセキュリティで保護する | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- denying My Reports folder access
- private folders [Reporting Services]
- user workspace [Reporting Services]
- security [Reporting Services], My Reports folder
- My Reports folder [Reporting Services]
ms.assetid: 3b23a382-13b8-4196-9a93-7fe62d03a63c
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: b0a832133852e05c54a80b73fad8a91426840467
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87713762"
---
# <a name="secure-my-reports"></a><span data-ttu-id="12e15-102">個人用レポートをセキュリティで保護する</span><span class="sxs-lookup"><span data-stu-id="12e15-102">Secure My Reports</span></span>
  <span data-ttu-id="12e15-103">個人用レポート機能により、ユーザーが管理するレポート処理用のワークスペースが提供されます。</span><span class="sxs-lookup"><span data-stu-id="12e15-103">The My Reports feature provides a user-managed workspace for working with reports.</span></span> <span data-ttu-id="12e15-104">[個人用レポート] フォルダーは、その性質上、他の汎用的な用途のフォルダーよりも権限の制限を緩める必要があります。</span><span class="sxs-lookup"><span data-stu-id="12e15-104">In order to serve its intended purpose, the My Reports folder requires less restrictive permissions than other folders that are available for general use.</span></span> <span data-ttu-id="12e15-105">他のフォルダーのレポートを表示および実行する権限しか持たないユーザーが、[個人用レポート] フォルダーおよび自らが所有するコンテンツを管理するためには、より強い権限が必要となります。</span><span class="sxs-lookup"><span data-stu-id="12e15-105">Users who have permissions to only view and run reports in other folders might require an expanded set of permissions to manage their My Reports folders and content that they own.</span></span> [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="12e15-106">には、そのための特別なロールの割り当てとロールの定義が用意されています。</span><span class="sxs-lookup"><span data-stu-id="12e15-106">provides a specialized role assignment and role definition for this purpose.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="12e15-107">個人用レポートはレポート マネージャーでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="12e15-107">My Reports is available only in Report Manager.</span></span> <span data-ttu-id="12e15-108">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]では使用できません。</span><span class="sxs-lookup"><span data-stu-id="12e15-108">It is not available in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].</span></span>  
  
## <a name="role-assignment-for-my-reports"></a><span data-ttu-id="12e15-109">個人用レポートのロールの割り当て</span><span class="sxs-lookup"><span data-stu-id="12e15-109">Role Assignment for My Reports</span></span>  
 <span data-ttu-id="12e15-110">個人用レポートのロールの割り当てには、あらかじめ要素が定義されています。[個人用レポート] フォルダーがアクティブになっている各ユーザーには、この割り当てが自動的に作成されます。</span><span class="sxs-lookup"><span data-stu-id="12e15-110">The role assignment for My Reports has preset elements and is automatically created for each user who activates a My Reports folder.</span></span> <span data-ttu-id="12e15-111">レポート サーバーから自動的にセキュリティを割り当てられるので、管理者が個人用レポートのユーザー 1 人ずつのアクセス権を有効にする必要がなくなります。したがって、個人用レポートを広く使用する組織にとっては、この手法が非常に有効です。</span><span class="sxs-lookup"><span data-stu-id="12e15-111">Having the report server automatically assign security is especially useful for organizations that use My Reports widely because administrators do not have to enable access for each My Reports user.</span></span>  
  
 <span data-ttu-id="12e15-112">**個人用レポート** ロールの割り当ては、次の要素で構成されています。</span><span class="sxs-lookup"><span data-stu-id="12e15-112">A **My Reports** role assignment consists of the following elements:</span></span>  
  
-   <span data-ttu-id="12e15-113">ユーザーの個人用レポートフォルダー。 [Users Folders \\ *\<username>* \My Reports] フォルダーにあります。</span><span class="sxs-lookup"><span data-stu-id="12e15-113">The user's My Reports folder, which is located in Users Folders\\*\<username>* \My Reports folder.</span></span>  
  
-   <span data-ttu-id="12e15-114">[個人用レポート] フォルダーをアクティブ化するときに判別されたユーザー アカウント。</span><span class="sxs-lookup"><span data-stu-id="12e15-114">The user account, which is determined when the My Reports folder is activated.</span></span> <span data-ttu-id="12e15-115">フォルダーがアクティブ化されるのは、ユーザーがレポート マネージャーの [個人用レポート] フォルダーをクリックするか、レポート デザイナーから [個人用レポート] フォルダーにレポートをパブリッシュしたときです。</span><span class="sxs-lookup"><span data-stu-id="12e15-115">A folder is activated when a user clicks a My Reports folder in Report Manager or when publishing a report to a My Reports folder from Report Designer.</span></span> <span data-ttu-id="12e15-116">ユーザーが [個人用レポート] リンクでプロパティを要求する場合も、このフォルダーはアクティブ化されます。</span><span class="sxs-lookup"><span data-stu-id="12e15-116">This folder is also activated when a user requests properties on the My Reports link.</span></span>  
  
-   <span data-ttu-id="12e15-117">個人用レポートの定義済みロールの定義。</span><span class="sxs-lookup"><span data-stu-id="12e15-117">The predefined role definition for My Reports.</span></span>  
  
## <a name="role-definition-for-my-reports"></a><span data-ttu-id="12e15-118">個人用レポートのロールの定義</span><span class="sxs-lookup"><span data-stu-id="12e15-118">Role Definition for My Reports</span></span>  
 <span data-ttu-id="12e15-119">個人用レポート ロールの定義には、 **[個人用レポート]** フォルダーのコンテンツ管理をサポートするタスクが含まれています。</span><span class="sxs-lookup"><span data-stu-id="12e15-119">The **My Reports** role definition includes tasks that support content management of a My Reports folder.</span></span> <span data-ttu-id="12e15-120">**個人用レポート** ロールは、専用の目的を持ったロールとして使用することを想定しています。</span><span class="sxs-lookup"><span data-stu-id="12e15-120">The **My Reports** role is intended to be a single-purpose role.</span></span> <span data-ttu-id="12e15-121">個人用レポート ロールはどのアイテムレベルのセキュリティ ポリシーに対しても選択できます。ただし、このロールの多用は避け、できるだけ他のフォルダー要件に合わせてこのロールを変更しないようにしてください。</span><span class="sxs-lookup"><span data-stu-id="12e15-121">Although you can choose it for any item-level security policy, you should avoid doing so to minimize the chance that you will modify it to accommodate other folder requirements.</span></span> <span data-ttu-id="12e15-122">個人用レポート機能に **個人用レポート** ロールを予約しておくことで、ユーザー間の使用環境を統一することができます。</span><span class="sxs-lookup"><span data-stu-id="12e15-122">Reserving the **My Reports** role for the My Reports feature can help you maintain a consistent experience for users.</span></span>  
  
 <span data-ttu-id="12e15-123">既定では、レポート サーバー管理者のみが **個人用レポート** ロールを変更します。</span><span class="sxs-lookup"><span data-stu-id="12e15-123">By default, only report server administrators modify the **My Reports** role.</span></span> <span data-ttu-id="12e15-124">**個人用レポート** ロールに含まれるタスクを変更することで、このロールをカスタマイズできます。</span><span class="sxs-lookup"><span data-stu-id="12e15-124">You can customize the **My Reports** role by changing the tasks it contains.</span></span> <span data-ttu-id="12e15-125">また、別のロールに置き換えることもできます。</span><span class="sxs-lookup"><span data-stu-id="12e15-125">You can also substitute a different role.</span></span>  
  
## <a name="denying-access-to-my-reports"></a><span data-ttu-id="12e15-126">個人用レポートへのアクセス拒否</span><span class="sxs-lookup"><span data-stu-id="12e15-126">Denying Access to My Reports</span></span>  
 <span data-ttu-id="12e15-127">ユーザーによる個人用レポートへのアクセスを拒否するには、次の方法を使用します。</span><span class="sxs-lookup"><span data-stu-id="12e15-127">You can prevent users from accessing My Reports by:</span></span>  
  
-   <span data-ttu-id="12e15-128">[サイトの設定] ページで個人用レポートを無効にします。</span><span class="sxs-lookup"><span data-stu-id="12e15-128">Disabling My Reports on the Site Settings page.</span></span> <span data-ttu-id="12e15-129">詳細については、 [「個人用レポートの有効化と無効化」](../report-server/enable-and-disable-my-reports.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="12e15-129">For more information, see [Enable and Disable My Reports](../report-server/enable-and-disable-my-reports.md).</span></span>  
  
-   <span data-ttu-id="12e15-130">**個人用レポート** ロールからすべてのタスクを削除します。</span><span class="sxs-lookup"><span data-stu-id="12e15-130">Removing all tasks from the **My Reports** role.</span></span>  
  
 <span data-ttu-id="12e15-131">個人用レポートを無効にすると、[個人用レポート] フォルダーのリンクがレポート マネージャーから削除されます。</span><span class="sxs-lookup"><span data-stu-id="12e15-131">When you disable My Reports, the link to a My Reports folder is removed from Report Manager.</span></span> <span data-ttu-id="12e15-132">個人用レポートをサポートする基本のフォルダー構造 (つまり Users フォルダーとサブフォルダー) は有効なままなので、ユーザーはフォルダーのパスがわかればアクセスすることができます。</span><span class="sxs-lookup"><span data-stu-id="12e15-132">The underlying folder structure that supports My Reports (that is, the Users Folders folder and subfolders) is still available and can be accessed if a user knows the folder path.</span></span> <span data-ttu-id="12e15-133">**個人用レポート** ロールからタスクを削除すると、アクセスが拒否されます。</span><span class="sxs-lookup"><span data-stu-id="12e15-133">Removing tasks from **My Reports** role ensures that access is prevented.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12e15-134">参照</span><span class="sxs-lookup"><span data-stu-id="12e15-134">See Also</span></span>  
 <span data-ttu-id="12e15-135">[レポートとリソースの保護](secure-reports-and-resources.md) </span><span class="sxs-lookup"><span data-stu-id="12e15-135">[Secure Reports and Resources](secure-reports-and-resources.md) </span></span>  
 <span data-ttu-id="12e15-136">[フォルダーをセキュリティで保護する](secure-folders.md) </span><span class="sxs-lookup"><span data-stu-id="12e15-136">[Secure Folders](secure-folders.md) </span></span>  
 [<span data-ttu-id="12e15-137">ネイティブ モードのレポート サーバーに対する権限の許可</span><span class="sxs-lookup"><span data-stu-id="12e15-137">Granting Permissions on a Native Mode Report Server</span></span>](granting-permissions-on-a-native-mode-report-server.md)  
  
  
