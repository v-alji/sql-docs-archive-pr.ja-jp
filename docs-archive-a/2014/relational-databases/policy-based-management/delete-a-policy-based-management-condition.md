---
title: ポリシー ベースの管理条件の削除 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Policy-Based Management, delete policy conditions
ms.assetid: e04148b8-f6dd-4c50-a5ef-c650b71dbf4d
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: f02a5294ecb53db4d8baa4f3dae0a232d9551a13
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631850"
---
# <a name="delete-a-policy-based-management-condition"></a><span data-ttu-id="52bfb-102">ポリシー ベースの管理条件の削除</span><span class="sxs-lookup"><span data-stu-id="52bfb-102">Delete a Policy-Based Management Condition</span></span>
  <span data-ttu-id="52bfb-103">このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] を使用して、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]でポリシー ベースの管理条件を削除する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="52bfb-103">This topic describes how to delete a Policy-based Management condition in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="52bfb-104">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="52bfb-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="52bfb-105">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="52bfb-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="52bfb-106">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="52bfb-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="52bfb-107">**以下を使用して条件を削除するには:**</span><span class="sxs-lookup"><span data-stu-id="52bfb-107">**To delete a condition, using:**</span></span>  
  
     [<span data-ttu-id="52bfb-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="52bfb-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="52bfb-109">はじめに</span><span class="sxs-lookup"><span data-stu-id="52bfb-109">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="52bfb-110">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="52bfb-110">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="52bfb-111">Permissions</span><span class="sxs-lookup"><span data-stu-id="52bfb-111">Permissions</span></span>  
 <span data-ttu-id="52bfb-112">msdb データベースの PolicyAdministratorRole ロールのメンバーシップが必要です。</span><span class="sxs-lookup"><span data-stu-id="52bfb-112">Requires membership in the PolicyAdministratorRole role in the msdb database.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="52bfb-113">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="52bfb-113">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-delete-a-condition"></a><span data-ttu-id="52bfb-114">条件を削除するには</span><span class="sxs-lookup"><span data-stu-id="52bfb-114">To delete a condition</span></span>  
  
1.  <span data-ttu-id="52bfb-115">**オブジェクト エクスプローラー**で、削除する条件を含むサーバーをプラス記号をクリックして展開します。</span><span class="sxs-lookup"><span data-stu-id="52bfb-115">In **Object Explorer**, click the plus sign to expand the server that contains the condition that you want to delete.</span></span>  
  
2.  <span data-ttu-id="52bfb-116">プラス記号をクリックして **[管理]** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="52bfb-116">Click the plus sign to expand the **Management** folder.</span></span>  
  
3.  <span data-ttu-id="52bfb-117">プラス記号をクリックして **[ポリシー管理]** を展開します。</span><span class="sxs-lookup"><span data-stu-id="52bfb-117">Click the plus sign to expand **Policy Management**.</span></span>  
  
4.  <span data-ttu-id="52bfb-118">プラス記号をクリックして **[条件]** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="52bfb-118">Click the plus sign to expand the **Conditions** folder.</span></span>  
  
5.  <span data-ttu-id="52bfb-119">削除する条件を右クリックして、 **[削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="52bfb-119">Right-click the condition that you want to delete and select **Delete**.</span></span>  
  
6.  <span data-ttu-id="52bfb-120">**[オブジェクトの削除]** ダイアログ ボックスで、正しい条件が選択されていることを確認し、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="52bfb-120">In the **Delete Object** dialog box, ensure that the correct condition is selected and then click **OK**.</span></span>  
  
  
