---
title: ロールとアクセス許可 (Reporting Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- access controls [Reporting Services]
- permissions [Reporting Services], about permissions
- security [Reporting Services], identity and access control
- authentication [Reporting Services]
- permissions [Reporting Services]
- security [Reporting Services], role-based
- identity [Reporting Services]
ms.assetid: eea655fe-43ed-418d-8233-b288a8f4daa4
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 0e6098a51afde04164e3ef0dfa5e5297457b4440
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641441"
---
# <a name="roles-and-permissions-reporting-services"></a><span data-ttu-id="b4abb-102">ロールと権限 (Reporting Services)</span><span class="sxs-lookup"><span data-stu-id="b4abb-102">Roles and Permissions (Reporting Services)</span></span>
  <span data-ttu-id="b4abb-103">Reporting Services では、認証サブシステムとロールベースの承認モデルを提供しています。</span><span class="sxs-lookup"><span data-stu-id="b4abb-103">Reporting Services provides an authentication subsystem and role-based authorization model.</span></span> <span data-ttu-id="b4abb-104">認証モデルと承認モデルは、レポート サーバーがネイティブ モードで実行されているか、SharePoint モードで実行されているかで異なります。</span><span class="sxs-lookup"><span data-stu-id="b4abb-104">Authentication and authorization models vary depending on whether the report server runs in native mode or SharePoint mode.</span></span> <span data-ttu-id="b4abb-105">レポート サーバーが SharePoint 配置の一部として存在している場合、SharePoint の権限によってレポート サーバーへのアクセス権を持つユーザーが決定されます。</span><span class="sxs-lookup"><span data-stu-id="b4abb-105">If the report server is part of a SharePoint deployment, SharePoint permissions determine who has access to the report server.</span></span>  
  
## <a name="identity-and-access-control-for-native-mode"></a><span data-ttu-id="b4abb-106">ネイティブ モードの ID およびアクセス制御</span><span class="sxs-lookup"><span data-stu-id="b4abb-106">Identity and Access Control for Native Mode</span></span>  
 <span data-ttu-id="b4abb-107">既定の認証は、Windows 認証および統合セキュリティに基づいています。</span><span class="sxs-lookup"><span data-stu-id="b4abb-107">Default authentication is based on Windows Authentication and integrated security.</span></span> <span data-ttu-id="b4abb-108">レポート サーバーが異なる認証要求に応答できるように認証設定を変更したり、既定のセキュリティ機能を、指定したカスタム認証拡張機能に置き換えたりすることができます。</span><span class="sxs-lookup"><span data-stu-id="b4abb-108">You can change the authentication settings to allow the report server to respond to different authentication requests, or even replace the default security features with a custom authentication extension that you provide.</span></span>  
  
 <span data-ttu-id="b4abb-109">承認は、プリンシパルに割り当てるロールに基づいています。</span><span class="sxs-lookup"><span data-stu-id="b4abb-109">Authorization is based on roles that you assign to a principle.</span></span> <span data-ttu-id="b4abb-110">各ロールは、一連の関連タスクで構成されており、タスクは関連操作で構成されています。</span><span class="sxs-lookup"><span data-stu-id="b4abb-110">Each role consists of a set of related tasks, which are in turn composed of related operations.</span></span> <span data-ttu-id="b4abb-111">たとえば、 **レポートの管理** タスクでは、レポートの表示、レポートの追加、レポートの更新、レポートの削除、レポートのスケジュール設定、レポート プロパティの更新という、レポート サーバーの操作へのアクセス権が付与されます。</span><span class="sxs-lookup"><span data-stu-id="b4abb-111">For example, the **Manage reports** task grants access to the following report server operations: view reports, add report, update report, delete report, schedule report, and update report properties.</span></span>  
  
## <a name="identity-and-access-control-for-sharepoint-mode"></a><span data-ttu-id="b4abb-112">SharePoint モードの ID およびアクセス制御</span><span class="sxs-lookup"><span data-stu-id="b4abb-112">Identity and Access Control for SharePoint Mode</span></span>  
 <span data-ttu-id="b4abb-113">SharePoint 統合モードでは、要求がレポート サーバーに到達する前に、認証と承認が SharePoint サイトで処理されます。</span><span class="sxs-lookup"><span data-stu-id="b4abb-113">In SharePoint integrated mode, authentication and authorization are handled on the SharePoint site, before requests reach the report server.</span></span> <span data-ttu-id="b4abb-114">認証の構成方法に応じて、SharePoint サイトからの要求には、セキュリティ トークンまたは信頼されたユーザー名が含まれます。</span><span class="sxs-lookup"><span data-stu-id="b4abb-114">Depending on how you configure authentication, requests from a SharePoint site include a security token or a trusted user name.</span></span> <span data-ttu-id="b4abb-115">SharePoint のユーザーおよびグループに設定した権限によって、SharePoint ライブラリに配置されているレポート サーバー アイテムへのアクセスが承認されます。</span><span class="sxs-lookup"><span data-stu-id="b4abb-115">Permissions that you set for SharePoint users and groups authorize access to report server items that are placed in SharePoint libraries.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b4abb-116">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="b4abb-116">In This Section</span></span>  
 [<span data-ttu-id="b4abb-117">ネイティブ モードのレポート サーバーに対する権限の許可</span><span class="sxs-lookup"><span data-stu-id="b4abb-117">Granting Permissions on a Native Mode Report Server</span></span>](granting-permissions-on-a-native-mode-report-server.md)  
 <span data-ttu-id="b4abb-118">コンテンツおよび操作へのアクセスを提供するロールベースの承認モデルについて説明します。</span><span class="sxs-lookup"><span data-stu-id="b4abb-118">Describes the role-based authorization model that provides access to content and operations.</span></span>  
  
 [<span data-ttu-id="b4abb-119">SharePoint サイトのレポート サーバー アイテムに対する権限の付与</span><span class="sxs-lookup"><span data-stu-id="b4abb-119">Granting Permissions on Report Server Items on a SharePoint Site</span></span>](granting-permissions-on-report-server-items-on-a-sharepoint-site.md)  
 <span data-ttu-id="b4abb-120">SharePoint グループ、権限レベル、および権限を使用してレポート サーバーへのアクセスを制御する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="b4abb-120">Explains how SharePoint groups, permission levels, and permissions are used to control access to a report server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4abb-121">参照</span><span class="sxs-lookup"><span data-stu-id="b4abb-121">See Also</span></span>  
 <span data-ttu-id="b4abb-122">[レポート サーバーでの認証](authentication-with-the-report-server.md) </span><span class="sxs-lookup"><span data-stu-id="b4abb-122">[Authentication with the Report Server](authentication-with-the-report-server.md) </span></span>  
 [<span data-ttu-id="b4abb-123">ネイティブ モードのレポート サーバーに対する権限の許可</span><span class="sxs-lookup"><span data-stu-id="b4abb-123">Granting Permissions on a Native Mode Report Server</span></span>](granting-permissions-on-a-native-mode-report-server.md)  
  
  
