---
title: システム管理者アカウントを変更する (マスターデータサービス) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- administrators [Master Data Services], changing
ms.assetid: cf30312e-4338-49a7-90f0-6e4f7b431ff8
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 1d13cdc19c70c9e16c92dfd290393739d7e4f5e9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87718369"
---
# <a name="change-the-system-administrator-account-master-data-services"></a><span data-ttu-id="828c3-102">システム管理者アカウントの変更 (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="828c3-102">Change the System Administrator Account (Master Data Services)</span></span>
  <span data-ttu-id="828c3-103">システム管理者として指定されているユーザーアカウントを変更することができ [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="828c3-103">You can change the user account that is designated as the [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] system administrator.</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="828c3-104">この手順が完了すると、前のシステム管理者のユーザー アカウントは削除されます。</span><span class="sxs-lookup"><span data-stu-id="828c3-104">When you complete this procedure, the former system administrator user account is deleted.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="828c3-105">前提条件</span><span class="sxs-lookup"><span data-stu-id="828c3-105">Prerequisites</span></span>  
 <span data-ttu-id="828c3-106">この手順を実行するには</span><span class="sxs-lookup"><span data-stu-id="828c3-106">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="828c3-107">新しい管理者のユーザー名を[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]のユーザーの一覧に追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="828c3-107">You must add the new administrator's user name to the [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] Users list.</span></span> <span data-ttu-id="828c3-108">詳細については、「 [Add a User &#40;マスターデータサービス&#41;](add-a-user-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="828c3-108">For more information, see [Add a User &#40;Master Data Services&#41;](add-a-user-master-data-services.md).</span></span>  
  
-   <span data-ttu-id="828c3-109">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] データベースで mdm.tblUser を表示して mdm.udpSecurityMemberProcessRebuildModel ストアド プロシージャを実行するための権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="828c3-109">You must have permission to view mdm.tblUser and to execute the mdm.udpSecurityMemberProcessRebuildModel stored procedure in the [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] database.</span></span> <span data-ttu-id="828c3-110">詳細については、「[データベース オブジェクト セキュリティ (マスター データ サービス)](../../2014/master-data-services/database-object-security-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="828c3-110">For more information, see [Database Object Security &#40;Master Data Services&#41;](../../2014/master-data-services/database-object-security-master-data-services.md).</span></span>  
  
### <a name="to-change-the-administrator-account"></a><span data-ttu-id="828c3-111">管理者アカウントを変更するには</span><span class="sxs-lookup"><span data-stu-id="828c3-111">To change the administrator account</span></span>  
  
1.  <span data-ttu-id="828c3-112">[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] を開き、 [!INCLUDE[ssDE](../includes/ssde-md.md)] データベースの [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] インスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="828c3-112">Open [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] and connect to the [!INCLUDE[ssDE](../includes/ssde-md.md)] instance for your [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] database.</span></span>  
  
2.  <span data-ttu-id="828c3-113">Mdm.tbluser で、新しい管理者となるユーザーを見つけて、列の値をコピーし `SID` ます。</span><span class="sxs-lookup"><span data-stu-id="828c3-113">In mdm.tblUser, find the user that will be the new administrator and copy the value in the `SID` column.</span></span>  
  
3.  <span data-ttu-id="828c3-114">新しいクエリを作成します。</span><span class="sxs-lookup"><span data-stu-id="828c3-114">Create a new query.</span></span>  
  
4.  <span data-ttu-id="828c3-115">次のテキストを入力し、*ドメイン \ user_name*を新しい管理者のユーザー名と*SID*に置き換え、手順 2. でコピーした値を使用します。</span><span class="sxs-lookup"><span data-stu-id="828c3-115">Type the following text, replacing *DOMAIN\user_name* with the new administrator's user name and *SID* with the value you copied in step 2.</span></span>  
  
    ```  
    EXEC [mdm].[udpSecuritySetAdministrator] @UserName='DOMAIN\user_name', @SID = 'SID', @PromoteNonAdmin = 1  
    ```  
  
5.  <span data-ttu-id="828c3-116">クエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="828c3-116">Run the query.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="828c3-117">参照</span><span class="sxs-lookup"><span data-stu-id="828c3-117">See Also</span></span>  
 [<span data-ttu-id="828c3-118">管理者 (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="828c3-118">Administrators &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/administrators-master-data-services.md)  
  
  
