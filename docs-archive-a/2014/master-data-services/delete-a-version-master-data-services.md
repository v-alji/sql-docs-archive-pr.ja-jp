---
title: バージョンを削除する (マスター データ サービス) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- versions [Master Data Services], deleting
- deleting versions [Master Data Services]
ms.assetid: 2a4eeffe-8379-4744-ad44-c27d8c8ac9a8
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: f83a3bc396b2a13ac7ac03ef653b16a0d556189a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645150"
---
# <a name="delete-a-version-master-data-services"></a><span data-ttu-id="08c41-102">バージョンを削除する (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="08c41-102">Delete a Version (Master Data Services)</span></span>
  <span data-ttu-id="08c41-103">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]で、バージョンに関連付けられたマスター データが確実に不要になった場合には、そのバージョンを削除します。</span><span class="sxs-lookup"><span data-stu-id="08c41-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], delete a version when you are sure you no longer need the master data associated with the version.</span></span> <span data-ttu-id="08c41-104">バージョンを削除した後、関連するマスター データを取得することはできません。</span><span class="sxs-lookup"><span data-stu-id="08c41-104">After you delete a version, you cannot retrieve the associated master data.</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="08c41-105">モデルにバージョンが 1 つしかない場合にそのバージョンを削除すると、モデルは使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="08c41-105">If a model has only one version and you delete it, the model becomes unusable.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="08c41-106">前提条件</span><span class="sxs-lookup"><span data-stu-id="08c41-106">Prerequisites</span></span>  
 <span data-ttu-id="08c41-107">この手順を実行するには</span><span class="sxs-lookup"><span data-stu-id="08c41-107">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="08c41-108">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] データベースで mdm.viw_SYSTEM_SCHEMA_VERSION ビューを表示して mds.udpVersionDelete ストアド プロシージャを実行するための権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="08c41-108">You must have permission to view the mdm.viw_SYSTEM_SCHEMA_VERSION view and to execute the mds.udpVersionDelete stored procedure in the [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] database.</span></span> <span data-ttu-id="08c41-109">詳細については、「[データベース オブジェクト セキュリティ (マスター データ サービス)](database-object-security-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="08c41-109">For more information, see [Database Object Security &#40;Master Data Services&#41;](database-object-security-master-data-services.md).</span></span>  
  
### <a name="to-delete-a-version"></a><span data-ttu-id="08c41-110">バージョンを削除するには</span><span class="sxs-lookup"><span data-stu-id="08c41-110">To delete a version</span></span>  
  
1.  <span data-ttu-id="08c41-111">[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] を開き、 [!INCLUDE[ssDE](../includes/ssde-md.md)] データベースの [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] インスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="08c41-111">Open [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] and connect to the [!INCLUDE[ssDE](../includes/ssde-md.md)] instance for your [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] database.</span></span>  
  
2.  <span data-ttu-id="08c41-112">mdm.viw_SYSTEM_SCHEMA_VERSION ビューを開きます。</span><span class="sxs-lookup"><span data-stu-id="08c41-112">Open the mdm.viw_SYSTEM_SCHEMA_VERSION view.</span></span>  
  
3.  <span data-ttu-id="08c41-113">削除するモデルのバージョンを見つけ、 **ID** フィールドの値をコピーします。</span><span class="sxs-lookup"><span data-stu-id="08c41-113">Find the version of the model you want to delete and copy the value in the **ID** field.</span></span>  
  
4.  <span data-ttu-id="08c41-114">新しいクエリを作成します。</span><span class="sxs-lookup"><span data-stu-id="08c41-114">Create a new query.</span></span>  
  
5.  <span data-ttu-id="08c41-115">次のテキストを入力します。その場合、 *version_ID* を手順 2 でコピーした値で置き換えます。</span><span class="sxs-lookup"><span data-stu-id="08c41-115">Type the following text, replacing *version_ID* with the value you copied in step 2.</span></span>  
  
    ```  
    EXEC [mdm].[udpVersionDelete] @Version_ID='version_ID'  
    ```  
  
6.  <span data-ttu-id="08c41-116">クエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="08c41-116">Run the query.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="08c41-117">Web アプリケーションに変更が反映されるまで数分かかる場合があります。</span><span class="sxs-lookup"><span data-stu-id="08c41-117">You may have to wait a few minutes before the Web application reflects the change.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08c41-118">参照</span><span class="sxs-lookup"><span data-stu-id="08c41-118">See Also</span></span>  
 <span data-ttu-id="08c41-119">[バージョン &#40;マスターデータサービス&#41;](../../2014/master-data-services/versions-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="08c41-119">[Versions &#40;Master Data Services&#41;](../../2014/master-data-services/versions-master-data-services.md) </span></span>  
 [<span data-ttu-id="08c41-120">バージョンをコピーする (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="08c41-120">Copy a Version &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/copy-a-version-master-data-services.md)  
  
  
