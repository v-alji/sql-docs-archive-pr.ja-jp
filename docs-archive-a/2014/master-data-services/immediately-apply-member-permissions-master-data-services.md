---
title: メンバー アクセス許可を直ちに適用する (マスター データ サービス) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- members [Master Data Services], applying permissions immediately
- permissions [Master Data Services], applying member permissions immediately
ms.assetid: 5b16de66-5c39-49f5-992f-402a9eb319aa
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: e960ad06213b7c5057a6249b72ce225a6abe35e2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642137"
---
# <a name="immediately-apply-member-permissions-master-data-services"></a><span data-ttu-id="5d18e-102">メンバー権限を直ちに適用する (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="5d18e-102">Immediately Apply Member Permissions (Master Data Services)</span></span>
  <span data-ttu-id="5d18e-103">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]で、メンバー セキュリティが定期的に適用されるのを待つ代わりに、メンバー権限を直ちに適用できます。</span><span class="sxs-lookup"><span data-stu-id="5d18e-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], instead of waiting for member security to be applied at regular intervals, you can apply member permissions immediately.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="5d18e-104">前提条件</span><span class="sxs-lookup"><span data-stu-id="5d18e-104">Prerequisites</span></span>  
 <span data-ttu-id="5d18e-105">この手順を実行するには</span><span class="sxs-lookup"><span data-stu-id="5d18e-105">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="5d18e-106">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] データベースで mdm.udpSecurityMemberProcessRebuildModel ストアド プロシージャを実行するための権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="5d18e-106">You must have permission to execute the mdm.udpSecurityMemberProcessRebuildModel stored procedure in the [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] database.</span></span> <span data-ttu-id="5d18e-107">詳細については、「[データベース オブジェクト セキュリティ (マスター データ サービス)](database-object-security-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5d18e-107">For more information, see [Database Object Security &#40;Master Data Services&#41;](database-object-security-master-data-services.md).</span></span>  
  
### <a name="to-immediately-apply-hierarchy-member-permissions"></a><span data-ttu-id="5d18e-108">階層メンバーの権限を直ちに適用するには</span><span class="sxs-lookup"><span data-stu-id="5d18e-108">To immediately apply hierarchy member permissions</span></span>  
  
1.  <span data-ttu-id="5d18e-109">[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] を開き、 [!INCLUDE[ssDE](../includes/ssde-md.md)] データベースの [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] インスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="5d18e-109">Open [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] and connect to the [!INCLUDE[ssDE](../includes/ssde-md.md)] instance for your [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] database.</span></span>  
  
2.  <span data-ttu-id="5d18e-110">新しいクエリを作成します。</span><span class="sxs-lookup"><span data-stu-id="5d18e-110">Create a new query.</span></span>  
  
3.  <span data-ttu-id="5d18e-111">次のテキストを入力します。その場合、 *database* をデータベースの名前で置き換え、 *Model_Name* をモデルの名前で置き換えます。</span><span class="sxs-lookup"><span data-stu-id="5d18e-111">Type the following text, replacing *database* with the name of your database and *Model_Name* with the name of the model.</span></span>  
  
    ```  
    USE [database];  
    GO  
  
    DECLARE @Model_ID INT;  
    SELECT @Model_ID = ID FROM mdm.tblModel WHERE [Name] = N'Model_Name';  
    EXEC [mdm].[udpSecurityMemberProcessRebuildModel] @Model_ID=@Model_ID, @ProcessNow=1;  
    GO  
    ```  
  
4.  <span data-ttu-id="5d18e-112">クエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="5d18e-112">Run the query.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d18e-113">参照</span><span class="sxs-lookup"><span data-stu-id="5d18e-113">See Also</span></span>  
 <span data-ttu-id="5d18e-114">[階層メンバーの権限を割り当てる &#40;マスターデータサービス&#41;](../../2014/master-data-services/assign-hierarchy-member-permissions-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="5d18e-114">[Assign Hierarchy Member Permissions &#40;Master Data Services&#41;](../../2014/master-data-services/assign-hierarchy-member-permissions-master-data-services.md) </span></span>  
 [<span data-ttu-id="5d18e-115">階層メンバーの権限 (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="5d18e-115">Hierarchy Member Permissions &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/hierarchy-member-permissions-master-data-services.md)  
  
  
