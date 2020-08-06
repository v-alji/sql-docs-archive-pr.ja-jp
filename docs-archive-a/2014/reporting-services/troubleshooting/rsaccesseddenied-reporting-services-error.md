---
title: rsAccessedDenied - Reporting Services エラー | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- rsAccessDenied error
ms.assetid: 2f76b1bf-96a2-4755-b76b-84e933220efc
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 194006c2ef6f22b9bc27e9e8cbe1eebd027ed6b5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641421"
---
# <a name="rsaccesseddenied---reporting-services-error"></a><span data-ttu-id="8de40-102">rsAccessedDenied - Reporting Services エラー</span><span class="sxs-lookup"><span data-stu-id="8de40-102">rsAccessedDenied - Reporting Services Error</span></span>
  <span data-ttu-id="8de40-103">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] エラー **rsAccessedDenied** は、操作を実行する権限がユーザーに与えられていない場合に発生します。</span><span class="sxs-lookup"><span data-stu-id="8de40-103">The [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] error **rsAccessedDenied** occurs when a user does not have permission to perform an action.</span></span> <span data-ttu-id="8de40-104">たとえば、レポートを開くためのロールが割り当てられていない場合や、必要な権限を使用してブラウザーを開かなかった場合などです。</span><span class="sxs-lookup"><span data-stu-id="8de40-104">For, example, they do not have a role assignment that allows them to open a report or they did not open their browser with the required permissions.</span></span>  
  
||  
|-|  
|<span data-ttu-id="8de40-105">**[!INCLUDE[applies](../../includes/applies-md.md)]** [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ネイティブ モード &#124; SharePoint モード</span><span class="sxs-lookup"><span data-stu-id="8de40-105">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Native mode &#124; SharePoint mode</span></span>|  
  
-   <span data-ttu-id="8de40-106">URL を指定してレポート サーバーへ直接アクセスしているときにこのエラーが発生した場合は、HTTP 401 エラーに例外がマップされます。</span><span class="sxs-lookup"><span data-stu-id="8de40-106">If the error occurred while accessing the report server directly through a URL, the exception is mapped to an HTTP 401 error.</span></span>  
  
-   <span data-ttu-id="8de40-107">レポート マネージャーやその他のツールを使用しているときに発生した場合は、エラー ページに表示されます。</span><span class="sxs-lookup"><span data-stu-id="8de40-107">If the error occurred while using Report Manager or another tool, the error appears in an error page.</span></span>  
  
-   <span data-ttu-id="8de40-108">スケジュール設定された操作、サブスクリプション、または配信中に発生した場合は、レポート サーバーのログ ファイルにのみ記録されます。</span><span class="sxs-lookup"><span data-stu-id="8de40-108">If the error occurred during a scheduled operation, subscription, or delivery, the error will appear in the report server log file only.</span></span>  
  
## <a name="details"></a><span data-ttu-id="8de40-109">詳細</span><span class="sxs-lookup"><span data-stu-id="8de40-109">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="8de40-110">**製品名**</span><span class="sxs-lookup"><span data-stu-id="8de40-110">**Product Name**</span></span>|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|<span data-ttu-id="8de40-111">**イベント ID**</span><span class="sxs-lookup"><span data-stu-id="8de40-111">**Event ID**</span></span>|<span data-ttu-id="8de40-112">rsAccessedDenied</span><span class="sxs-lookup"><span data-stu-id="8de40-112">rsAccessedDenied</span></span>|  
|<span data-ttu-id="8de40-113">**イベント ソース**</span><span class="sxs-lookup"><span data-stu-id="8de40-113">**Event Source**</span></span>|<span data-ttu-id="8de40-114">Microsoft.ReportingServices.Diagnostics.Utilities.ErrorStrings</span><span class="sxs-lookup"><span data-stu-id="8de40-114">Microsoft.ReportingServices.Diagnostics.Utilities.ErrorStrings</span></span>|  
|<span data-ttu-id="8de40-115">**コンポーネント**</span><span class="sxs-lookup"><span data-stu-id="8de40-115">**Component**</span></span>|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]|  
|<span data-ttu-id="8de40-116">**メッセージ テキスト**</span><span class="sxs-lookup"><span data-stu-id="8de40-116">**Message Text**</span></span>|<span data-ttu-id="8de40-117">ユーザー 'mydomain\myAccount' には、この操作を行うのに必要な権限が与えられていません。</span><span class="sxs-lookup"><span data-stu-id="8de40-117">The permissions granted to user 'mydomain\myAccount' are insufficient for performing this operation.</span></span> <span data-ttu-id="8de40-118">(rsAccessDenied) (ReportingServicesLibrary)。</span><span class="sxs-lookup"><span data-stu-id="8de40-118">(rsAccessDenied) (ReportingServicesLibrary)</span></span>|  
  
## <a name="user-action"></a><span data-ttu-id="8de40-119">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="8de40-119">User Action</span></span>  
 <span data-ttu-id="8de40-120">レポート サーバーのコンテンツや操作にアクセスする権限は、ロールの割り当てによって与えられます。</span><span class="sxs-lookup"><span data-stu-id="8de40-120">Permission to access report server content and operations are granted through role assignments.</span></span> <span data-ttu-id="8de40-121">新規インストールを実行した時点では、ローカル管理者のみがレポート サーバーにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="8de40-121">On a new installation, only local administrators have access to a report server.</span></span> <span data-ttu-id="8de40-122">他のユーザーがレポート サーバーにアクセスできるようにするには、ローカル管理者が、ドメインのユーザー アカウントやグループ アカウントを指定するロールの割り当て、ユーザーが実行できるタスクを定義する 1 つ以上のロール、およびスコープ (通常は、レポート サーバー フォルダー階層のルート ノードである [ホーム] フォルダー) を作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8de40-122">To grant access to other users, a local administrator must create a role assignment that specifies a domain user or group account, one or more roles that define the tasks the user can perform, and a scope (usually the Home folder or root node of the report server folder hierarchy).</span></span> <span data-ttu-id="8de40-123">レポート マネージャーを使用すると、ロールの割り当てを作成できます。</span><span class="sxs-lookup"><span data-stu-id="8de40-123">You can use Report Manager to create the role assignments.</span></span> <span data-ttu-id="8de40-124">詳細については、SQL Server オンライン ブックの「ロールの割り当て」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8de40-124">For more information, search for "Role Assignments" in SQL Server Books Online.</span></span>  
  
 <span data-ttu-id="8de40-125">このエラーは、レポート サーバーのローカル管理が原因で発生することもあります。</span><span class="sxs-lookup"><span data-stu-id="8de40-125">This error is also caused by local administration of the report server.</span></span> <span data-ttu-id="8de40-126">詳細については、「 [ローカル管理用のネイティブ モードのレポート サーバー &#40;SSRS&#41; の構成](../report-server/configure-a-native-mode-report-server-for-local-administration-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8de40-126">For more information, see [Configure a Native Mode Report Server for Local Administration &#40;SSRS&#41;](../report-server/configure-a-native-mode-report-server-for-local-administration-ssrs.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8de40-127">参照</span><span class="sxs-lookup"><span data-stu-id="8de40-127">See Also</span></span>  
 <span data-ttu-id="8de40-128">[ロールの割り当て](../security/role-assignments.md) </span><span class="sxs-lookup"><span data-stu-id="8de40-128">[Role Assignments](../security/role-assignments.md) </span></span>  
 <span data-ttu-id="8de40-129">[ネイティブ モードのレポート サーバーに対する権限の許可](../security/granting-permissions-on-a-native-mode-report-server.md) </span><span class="sxs-lookup"><span data-stu-id="8de40-129">[Granting Permissions on a Native Mode Report Server](../security/granting-permissions-on-a-native-mode-report-server.md) </span></span>  
 [<span data-ttu-id="8de40-130">ロールと権限 &#40;Reporting Services&#41;</span><span class="sxs-lookup"><span data-stu-id="8de40-130">Roles and Permissions &#40;Reporting Services&#41;</span></span>](../security/roles-and-permissions-reporting-services.md)  
  
  
