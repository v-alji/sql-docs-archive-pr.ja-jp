---
title: テーブルモデルデータベースに対するメモリ内または DirectQuery アクセスの構成 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: a5d439a9-5be1-4145-90e8-90777d80e98b
author: minewiskan
ms.author: owend
ms.openlocfilehash: a607bc6c11f35736487932bdf10d239afc8b5355
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87712521"
---
# <a name="configure-in-memory-or-directquery-access-for-a-tabular-model-database"></a><span data-ttu-id="57445-102">テーブル モデルのデータベースの In-Memory または DirectQuery アクセスの構成</span><span class="sxs-lookup"><span data-stu-id="57445-102">Configure In-Memory or DirectQuery Access for a Tabular Model Database</span></span>
  <span data-ttu-id="57445-103">このトピックでは、既に配置されたテーブル モデルの接続プロパティを変更し、モデルを直接クエリ モードで使用できるようにする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="57445-103">This topic describes how to change the connection properties of a tabular model that has already been deployed, to enable use of the model in Direct Query mode.</span></span>  
  
 <span data-ttu-id="57445-104">これらのプロパティ、および最も一般的なシナリオの構成の詳細については、「 [SSAS のデプロイシナリオ &#40;SSAS 表形式&#41;](../directquery-deployment-scenarios-ssas-tabular.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="57445-104">For more information about these properties, and configuration for the most common scenarios, see [DirectQuery Deployment Scenarios &#40;SSAS Tabular&#41;](../directquery-deployment-scenarios-ssas-tabular.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="57445-105">必要条件</span><span class="sxs-lookup"><span data-stu-id="57445-105">Requirements</span></span>  
 <span data-ttu-id="57445-106">テーブル モデルで直接クエリ モードを使用できるようにする操作は、複数の手順から成るプロセスです。</span><span class="sxs-lookup"><span data-stu-id="57445-106">Enabling the use of Direct Query mode on a tabular model is a multistep process.</span></span> <span data-ttu-id="57445-107">次の手順が必要です。</span><span class="sxs-lookup"><span data-stu-id="57445-107">You must:</span></span>  
  
1.  <span data-ttu-id="57445-108">直接クエリ モードで検証エラーが発生するような機能がモデルにないことを確認します。</span><span class="sxs-lookup"><span data-stu-id="57445-108">Ensure that the model does not have features which might cause validation errors in Direct Query mode.</span></span>  
  
2.  <span data-ttu-id="57445-109">直接クエリをサポートするように、モデルのストレージ モードを変更します。</span><span class="sxs-lookup"><span data-stu-id="57445-109">Change the storage mode on the model to support Direct Query.</span></span>  
  
3.  <span data-ttu-id="57445-110">ハイブリッド モードと純粋な直接クエリ モードの両方のクエリをサポートするモードでモデルを配置します。</span><span class="sxs-lookup"><span data-stu-id="57445-110">Deploy the model in a mode that supports queries in either a hybrid or pure Direct Query mode.</span></span>  
  
4.  <span data-ttu-id="57445-111">配置されたデータベースの接続文字列を、直接クエリ モードをサポートするように編集します。</span><span class="sxs-lookup"><span data-stu-id="57445-111">Edit the connection string on the deployed database to support Direct Query mode.</span></span>  
  
 <span data-ttu-id="57445-112">このトピックは、モデルが既に作成および検証済みで、[!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] などのクライアントからの直接クエリ アクセスの有効化だけが必要であることを前提としています。</span><span class="sxs-lookup"><span data-stu-id="57445-112">This topic assumes that you have created and validated your model, and only need to enable Direct Query access from a client such as [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)].</span></span>  
  
## <a name="procedure"></a><span data-ttu-id="57445-113">手順</span><span class="sxs-lookup"><span data-stu-id="57445-113">Procedure</span></span>  
  
#### <a name="change-the-connection-string-properties-of-the-model"></a><span data-ttu-id="57445-114">モデルの接続文字列プロパティの変更</span><span class="sxs-lookup"><span data-stu-id="57445-114">Change the Connection String Properties of the Model</span></span>  
  
1.  <span data-ttu-id="57445-115">SQLServer Management Studio で、モデルを配置するインスタンスを開きます。</span><span class="sxs-lookup"><span data-stu-id="57445-115">In SQL Server Management Studio, open the instance to which you deployed the model.</span></span>  
  
2.  <span data-ttu-id="57445-116">オブジェクトエクスプローラーで、モデルデータベースの名前を右クリックし、[**プロパティ**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="57445-116">In Object Explorer, right-click the name of the model database, and select **Properties**.</span></span>  
  
3.  <span data-ttu-id="57445-117">**Directquerymode**プロパティを見つけます。</span><span class="sxs-lookup"><span data-stu-id="57445-117">Locate the property, **DirectQueryMode**.</span></span> <span data-ttu-id="57445-118">リレーショナル データ ソースを使用できるようにするには、このプロパティを次のいずれかの値に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="57445-118">To enable use of the relational data source, this property must be set to one of these values:</span></span>  
  
    -   <span data-ttu-id="57445-119">**DirectQuery**</span><span class="sxs-lookup"><span data-stu-id="57445-119">**DirectQuery**</span></span>  
  
    -   <span data-ttu-id="57445-120">**InMemoryWithDirectQuery**</span><span class="sxs-lookup"><span data-stu-id="57445-120">**InMemoryWithDirectQuery**</span></span>  
  
    -   <span data-ttu-id="57445-121">**DirectQueryWithInMemory**</span><span class="sxs-lookup"><span data-stu-id="57445-121">**DirectQueryWithInMemory**</span></span>  
  
  
