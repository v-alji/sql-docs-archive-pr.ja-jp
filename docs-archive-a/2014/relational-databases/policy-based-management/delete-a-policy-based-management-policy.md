---
title: ポリシー ベースの管理ポリシーの削除 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Policy-Based Management, delete policies
ms.assetid: 488f0305-190c-4223-aa5c-e9bd43b520eb
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 7c43bc3cdf4a7a5b5d9268bbd7e68506616d1f0f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87711890"
---
# <a name="delete-a-policy-based-management-policy"></a><span data-ttu-id="4ba81-102">ポリシー ベースの管理ポリシーの削除</span><span class="sxs-lookup"><span data-stu-id="4ba81-102">Delete a Policy-Based Management Policy</span></span>
  <span data-ttu-id="4ba81-103">このトピックでは、[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] または [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] を使用して、[!INCLUDE[tsql](../../includes/tsql-md.md)] でポリシー ベースの管理ポリシーを削除する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="4ba81-103">This topic describes how to delete a Policy-Based Management policy in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="4ba81-104">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="4ba81-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="4ba81-105">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="4ba81-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="4ba81-106">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="4ba81-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="4ba81-107">**以下を使用してポリシーを削除するには:**</span><span class="sxs-lookup"><span data-stu-id="4ba81-107">**To delete a policy, using:**</span></span>  
  
     [<span data-ttu-id="4ba81-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="4ba81-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="4ba81-109">はじめに</span><span class="sxs-lookup"><span data-stu-id="4ba81-109">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="4ba81-110">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="4ba81-110">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="4ba81-111">Permissions</span><span class="sxs-lookup"><span data-stu-id="4ba81-111">Permissions</span></span>  
 <span data-ttu-id="4ba81-112">msdb データベースの PolicyAdministratorRole ロールのメンバーシップが必要です。</span><span class="sxs-lookup"><span data-stu-id="4ba81-112">Requires membership in the PolicyAdministratorRole role in the msdb database.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="4ba81-113">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="4ba81-113">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-delete-a-policy"></a><span data-ttu-id="4ba81-114">ポリシーを削除するには</span><span class="sxs-lookup"><span data-stu-id="4ba81-114">To delete a policy</span></span>  
  
1.  <span data-ttu-id="4ba81-115">オブジェクト エクスプローラーで、削除するポリシー ベースの管理ポリシーを含むサーバーをプラス記号をクリックして展開します。</span><span class="sxs-lookup"><span data-stu-id="4ba81-115">In Object Explorer, click the plus sign to expand the server that contains the Policy-Based Management policy that you want to delete.</span></span>  
  
2.  <span data-ttu-id="4ba81-116">プラス記号をクリックして **[管理]** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="4ba81-116">Click the plus sign to expand the **Management** folder.</span></span>  
  
3.  <span data-ttu-id="4ba81-117">プラス記号をクリックして **[ポリシー管理]** を展開します。</span><span class="sxs-lookup"><span data-stu-id="4ba81-117">Click the plus sign to expand **Policy Management**.</span></span>  
  
4.  <span data-ttu-id="4ba81-118">プラス記号をクリックして **[ポリシー]** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="4ba81-118">Click the plus sign to expand the **Policies** folder.</span></span>  
  
5.  <span data-ttu-id="4ba81-119">削除するポリシーを右クリックして、 **[削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4ba81-119">Right-click the policy that you want to delete and select **Delete**.</span></span>  
  
6.  <span data-ttu-id="4ba81-120">**[オブジェクトの削除]** ダイアログ ボックスで、正しい条件が選択されていることを確認し、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4ba81-120">In the **Delete Object** dialog box, ensure that the correct condition is selected and then click **OK**.</span></span>  
  
  
