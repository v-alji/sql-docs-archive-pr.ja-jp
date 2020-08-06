---
title: ステージング処理中に発生したエラーの表示 (マスターデータサービス) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- staging process [Master Data Services], viewing errors
ms.assetid: 6d2bff84-624b-47fc-a4a5-d9ea01d13412
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 3b39d039b29090f3021c764126ebb782ce25cbfe
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87715473"
---
# <a name="view-errors-that-occur-during-the-staging-process-master-data-services"></a><span data-ttu-id="26a48-102">ステージング処理中に発生したエラーの表示 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="26a48-102">View Errors that Occur During the Staging Process (Master Data Services)</span></span>
  <span data-ttu-id="26a48-103">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]では、ステージング処理中に発生したエラーを表示できます。</span><span class="sxs-lookup"><span data-stu-id="26a48-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], you can view errors that occur during the staging process.</span></span> <span data-ttu-id="26a48-104">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] データベースには、エラーを表示する 2 つのビューがあります。</span><span class="sxs-lookup"><span data-stu-id="26a48-104">In the [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] database, there are two views that show errors:</span></span>  
  
-   <span data-ttu-id="26a48-105">stg.viw_name_MemberErrorDetails (リーフ メンバーまたは統合メンバーの更新用)。</span><span class="sxs-lookup"><span data-stu-id="26a48-105">stg.viw_name_MemberErrorDetails for leaf or consolidated member updates.</span></span>  
  
-   <span data-ttu-id="26a48-106">stg.viw_name_RelationshipErrorDetails (階層のリレーションシップの更新用)。</span><span class="sxs-lookup"><span data-stu-id="26a48-106">stg.viw_name_RelationshipErrorDetails for hierarchy relationship updates.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="26a48-107">前提条件</span><span class="sxs-lookup"><span data-stu-id="26a48-107">Prerequisites</span></span>  
 <span data-ttu-id="26a48-108">この手順を実行するには</span><span class="sxs-lookup"><span data-stu-id="26a48-108">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="26a48-109">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] データベースでは、stg.viw_name_MemberErrorDetails ビューまたは stg.viw_name_RelationshipErrorDetails ビューのどちらかに対する SELECT 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="26a48-109">In the [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] database, you must have SELECT permissions to either the stg.viw_name_MemberErrorDetails or stg.viw_name_RelationshipErrorDetails view.</span></span>  
  
-   <span data-ttu-id="26a48-110">モデル管理者である必要があります。</span><span class="sxs-lookup"><span data-stu-id="26a48-110">You must be a model administrator.</span></span> <span data-ttu-id="26a48-111">詳細については、「[管理者 &#40;マスターデータサービス&#41;](administrators-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="26a48-111">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
### <a name="to-view-staging-errors"></a><span data-ttu-id="26a48-112">ステージング エラーを表示するには</span><span class="sxs-lookup"><span data-stu-id="26a48-112">To view staging errors</span></span>  
  
1.  <span data-ttu-id="26a48-113">[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] を開き、 [!INCLUDE[ssDE](../includes/ssde-md.md)] データベースの [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] インスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="26a48-113">Open [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] and connect to the [!INCLUDE[ssDE](../includes/ssde-md.md)] instance for your [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] database.</span></span>  
  
2.  <span data-ttu-id="26a48-114">新しいクエリを開きます。</span><span class="sxs-lookup"><span data-stu-id="26a48-114">Open a new query.</span></span>  
  
3.  <span data-ttu-id="26a48-115">名前を viw_Product_MemberErrorDetails などのステージング テーブルの名前に置き換えて、次のテキストを入力します。</span><span class="sxs-lookup"><span data-stu-id="26a48-115">Type the following text, replacing name with the name of your staging table, for example, viw_Product_MemberErrorDetails.</span></span>  
  
     `SELECT * FROM stg.viw_name_MemberErrorDetails`  
  
4.  <span data-ttu-id="26a48-116">クエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="26a48-116">Excecute the query.</span></span> <span data-ttu-id="26a48-117">エラーの詳細が **ErrorDescription** フィールドに表示されます。</span><span class="sxs-lookup"><span data-stu-id="26a48-117">Error details are displayed in the **ErrorDescription** field.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="26a48-118">次の手順</span><span class="sxs-lookup"><span data-stu-id="26a48-118">Next Steps</span></span>  
 <span data-ttu-id="26a48-119">エラー メッセージの詳細については、「[ステージング処理のエラー (マスター データ サービス)](../../2014/master-data-services/staging-process-errors-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="26a48-119">For more details on error messages, see [Staging Process Errors &#40;Master Data Services&#41;](../../2014/master-data-services/staging-process-errors-master-data-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26a48-120">参照</span><span class="sxs-lookup"><span data-stu-id="26a48-120">See Also</span></span>  
 <span data-ttu-id="26a48-121">[データのインポート &#40;マスターデータサービス&#41;](overview-importing-data-from-tables-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="26a48-121">[Data Import &#40;Master Data Services&#41;](overview-importing-data-from-tables-master-data-services.md) </span></span>  
 [<span data-ttu-id="26a48-122">ステージング処理のトラブルシューティング (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="26a48-122">Troubleshooting the Staging Process (Master Data Services)</span></span>](https://social.technet.microsoft.com/wiki/contents/articles/troubleshooting-the-staging-process-master-data-services.aspx)  
  
  
