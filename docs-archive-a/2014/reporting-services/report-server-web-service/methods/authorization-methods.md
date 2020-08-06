---
title: Authorization メソッド | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- security [Reporting Services], reports
- authorization [Reporting Services]
- reports [Reporting Services], security
- tasks [Reporting Services]
- roles [Reporting Services], methods
ms.assetid: 45e9cf2c-facf-4801-9482-c855403f42a8
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: b04a21b5075e939a4732e2f8ec219e169f4ba440
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87721099"
---
# <a name="authorization-methods"></a><span data-ttu-id="dc80b-102">Authorization メソッド</span><span class="sxs-lookup"><span data-stu-id="dc80b-102">Authorization Methods</span></span>
  <span data-ttu-id="dc80b-103">以下のメソッドを使用して、レポート サーバーでタスク、ロール、およびポリシーを管理できます。</span><span class="sxs-lookup"><span data-stu-id="dc80b-103">You can use these methods to manage tasks, roles, and policies on the report server.</span></span>  
  
|<span data-ttu-id="dc80b-104">Method</span><span class="sxs-lookup"><span data-stu-id="dc80b-104">Method</span></span>|<span data-ttu-id="dc80b-105">アクション</span><span class="sxs-lookup"><span data-stu-id="dc80b-105">Action</span></span>|  
|------------|------------|  
|<xref:ReportService2010.ReportingService2010.CreateRole%2A>|<span data-ttu-id="dc80b-106">新しいロールをレポート サーバー データベースに追加します。</span><span class="sxs-lookup"><span data-stu-id="dc80b-106">Adds a new role to the report server database.</span></span> <span data-ttu-id="dc80b-107">このメソッドはネイティブ モードにのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="dc80b-107">This method =applies to native mode only.</span></span>|  
|<xref:ReportService2010.ReportingService2010.DeleteRole%2A>|<span data-ttu-id="dc80b-108">レポート サーバー データベースからロールを削除します。</span><span class="sxs-lookup"><span data-stu-id="dc80b-108">Deletes a role from the report server database.</span></span> <span data-ttu-id="dc80b-109">このメソッドはネイティブ モードにのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="dc80b-109">This method applies to native mode only.</span></span>|  
|<xref:ReportService2010.ReportingService2010.GetPermissions%2A>|<span data-ttu-id="dc80b-110">レポート サーバー データベースまたは SharePoint ライブラリの特定のアイテムに関連付けられたユーザー アクセス許可を返します。</span><span class="sxs-lookup"><span data-stu-id="dc80b-110">Returns the user permissions that are associated with a particular item in the report server database or SharePoint library.</span></span>|  
|<xref:ReportService2010.ReportingService2010.GetPolicies%2A>|<span data-ttu-id="dc80b-111">レポート サーバー データベースまたは SharePoint ライブラリの特定のアイテムに関連付けられたポリシーを返します。</span><span class="sxs-lookup"><span data-stu-id="dc80b-111">Returns the policies that are associated with a particular item in the report server database or SharePoint library.</span></span>|  
|<xref:ReportService2010.ReportingService2010.GetRoleProperties%2A>|<span data-ttu-id="dc80b-112">ロールのメタデータ プロパティと関連付けられたタスクのコレクションを返します。</span><span class="sxs-lookup"><span data-stu-id="dc80b-112">Returns role metadata properties and a collection of associated tasks.</span></span>|  
|<xref:ReportService2010.ReportingService2010.GetSystemPermissions%2A>|<span data-ttu-id="dc80b-113">ユーザーのシステム権限を返します。</span><span class="sxs-lookup"><span data-stu-id="dc80b-113">Returns the user's system permissions.</span></span> <span data-ttu-id="dc80b-114">このメソッドはネイティブ モードにのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="dc80b-114">This method applies to native mode only.</span></span>|  
|<xref:ReportService2010.ReportingService2010.GetSystemPolicies%2A>|<span data-ttu-id="dc80b-115">システム ポリシーに関連付けられるグループとロールを含むシステム ポリシーを返します。</span><span class="sxs-lookup"><span data-stu-id="dc80b-115">Returns the system policies, including groups and roles with which they are associated.</span></span> <span data-ttu-id="dc80b-116">このメソッドはネイティブ モードにのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="dc80b-116">This method applies to native mode only.</span></span>|  
|<xref:ReportService2010.ReportingService2010.InheritParentSecurity%2A>|<span data-ttu-id="dc80b-117">レポート サーバー データベースの特定のアイテムに関連付けられたポリシーを削除し、アイテムのセキュリティ ポリシーをアイテムの親のセキュリティ ポリシーに設定します。</span><span class="sxs-lookup"><span data-stu-id="dc80b-117">Deletes the policies that are associated with a particular item in the report server database and sets the security policies for the item to those of its parent.</span></span>|  
|<xref:ReportService2010.ReportingService2010.IsSSLRequired%2A>|<span data-ttu-id="dc80b-118"><xref:ReportService2010> エンドポイントを使用するために SSL (Secure Sockets Layer) プロトコルが必要かどうかを示すブール値を返します。</span><span class="sxs-lookup"><span data-stu-id="dc80b-118">Returns a Boolean value that indicates whether the Secure Socket Layer (SSL) protocol is required to use the <xref:ReportService2010> end point.</span></span>|  
|<xref:ReportService2010.ReportingService2010.ListRoles%2A>|<span data-ttu-id="dc80b-119">レポート サーバーによって管理されるロールの名前と説明を返します。</span><span class="sxs-lookup"><span data-stu-id="dc80b-119">Returns the names and descriptions of roles that are managed by the report server.</span></span>|  
|<xref:ReportExecution2005.ReportExecutionService.ListSecureMethods%2A>|<span data-ttu-id="dc80b-120">呼び出し時にセキュリティで保護された接続が必要な、<xref:ReportExecution2005> エンドポイントの Simple Object Access Protocol (SOAP) メソッドの一覧を返します。</span><span class="sxs-lookup"><span data-stu-id="dc80b-120">Returns a list of Simple Object Access Protocol (SOAP) methods in the <xref:ReportExecution2005> endpoint that require a secure connection when invoked.</span></span> <span data-ttu-id="dc80b-121">レポート サーバーの `SecureConnectionLevel` 設定を使用して、どのメソッドを返すかを判断します。</span><span class="sxs-lookup"><span data-stu-id="dc80b-121">The `SecureConnectionLevel` setting of the report server is used to determine which methods are returned.</span></span>|  
|<xref:ReportService2010.ReportingService2010.ListTasks%2A>|<span data-ttu-id="dc80b-122">レポート サーバーが管理するタスクを返します。</span><span class="sxs-lookup"><span data-stu-id="dc80b-122">Returns the tasks that are managed by the report server.</span></span>|  
|<xref:ReportService2010.ReportingService2010.SetPolicies%2A>|<span data-ttu-id="dc80b-123">指定したアイテムに関連付けられたポリシーを設定します。</span><span class="sxs-lookup"><span data-stu-id="dc80b-123">Sets the policies that are associated with a specified item.</span></span>|  
|<xref:ReportService2010.ReportingService2010.SetRoleProperties%2A>|<span data-ttu-id="dc80b-124">ロールのメタデータ プロパティを設定し、一連のタスクをロールに関連付けます。</span><span class="sxs-lookup"><span data-stu-id="dc80b-124">Sets role metadata properties and associates a set of tasks with a role.</span></span> <span data-ttu-id="dc80b-125">このメソッドはネイティブ モードにのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="dc80b-125">This method applies to native mode only.</span></span>|  
|<xref:ReportService2010.ReportingService2010.SetSystemPolicies%2A>|<span data-ttu-id="dc80b-126">グループと、それらに関連付けられたロールを定義するシステム ポリシーを設定します。</span><span class="sxs-lookup"><span data-stu-id="dc80b-126">Sets the system policy that defines groups and their associated roles.</span></span> <span data-ttu-id="dc80b-127">このメソッドはネイティブ モードにのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="dc80b-127">This method applies to native mode only.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="dc80b-128">参照</span><span class="sxs-lookup"><span data-stu-id="dc80b-128">See Also</span></span>  
 <span data-ttu-id="dc80b-129">[Web サービスと .NET Framework を使用してのアプリケーションの構築](../net-framework/building-applications-using-the-web-service-and-the-net-framework.md) </span><span class="sxs-lookup"><span data-stu-id="dc80b-129">[Building Applications Using the Web Service and the .NET Framework](../net-framework/building-applications-using-the-web-service-and-the-net-framework.md) </span></span>  
 <span data-ttu-id="dc80b-130">[レポート サーバー Web サービス](../report-server-web-service.md) </span><span class="sxs-lookup"><span data-stu-id="dc80b-130">[Report Server Web Service](../report-server-web-service.md) </span></span>  
 <span data-ttu-id="dc80b-131">[レポート サーバー Web サービス メソッド](report-server-web-service-methods.md) </span><span class="sxs-lookup"><span data-stu-id="dc80b-131">[Report Server Web Service Methods](report-server-web-service-methods.md) </span></span>  
 [<span data-ttu-id="dc80b-132">テクニカル リファレンス (SSRS)</span><span class="sxs-lookup"><span data-stu-id="dc80b-132">Technical Reference &#40;SSRS&#41;</span></span>](../../technical-reference-ssrs.md)  
  
  
