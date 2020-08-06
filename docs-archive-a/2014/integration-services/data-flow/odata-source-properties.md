---
title: OData ソースのプロパティ | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 4fde5bb0-6d78-4ec4-8f0b-67f91c53fe99
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 8139f79ed595ca3e6204f96823f6bc95e6fb40df
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741141"
---
# <a name="odata-source-properties"></a><span data-ttu-id="4137a-102">OData ソースのプロパティ</span><span class="sxs-lookup"><span data-stu-id="4137a-102">OData Source Properties</span></span>
  <span data-ttu-id="4137a-103">データ フローで **[OData ソース]** を右クリックし、 **[プロパティ]** をクリックすると、 **[プロパティ]** ウィンドウに **[OData ソース]** コンポーネントに対応するプロパティが表示されます。</span><span class="sxs-lookup"><span data-stu-id="4137a-103">When you right-click **OData Source** in the data flow and click **Properties**, you will see properties for the **OData Source** component in the **Properties** window.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="4137a-104">プロパティ</span><span class="sxs-lookup"><span data-stu-id="4137a-104">Property</span></span>|<span data-ttu-id="4137a-105">説明</span><span class="sxs-lookup"><span data-stu-id="4137a-105">Description</span></span>|  
|<span data-ttu-id="4137a-106">CollectionName</span><span class="sxs-lookup"><span data-stu-id="4137a-106">CollectionName</span></span>|<span data-ttu-id="4137a-107">OData サービスから取得するコレクションの名前。</span><span class="sxs-lookup"><span data-stu-id="4137a-107">Name of the collection you wish to retrieve from the OData service.</span></span> <span data-ttu-id="4137a-108">**[CollectionName]** プロパティは、 **UseResourcePath** が FALSE の場合に使用されます。</span><span class="sxs-lookup"><span data-stu-id="4137a-108">The **CollectionName** property is used when **UseResourcePath** is False.</span></span><br /><br /> <span data-ttu-id="4137a-109">このプロパティは式にすることができ、その結果、実行時に値を設定することができます。</span><span class="sxs-lookup"><span data-stu-id="4137a-109">This property is expression-able, allowing the value to be set at runtime.</span></span> <span data-ttu-id="4137a-110">ただし、コレクションのメタデータが、デザイン時に使用したメタデータと一致しない場合は、検証エラーが発生し、データ フローの実行が失敗します。</span><span class="sxs-lookup"><span data-stu-id="4137a-110">However, if the metadata of the collection does not match the metadata that was used at design time, a validation error will occur, causing the data flow execution to fail.</span></span>|  
|<span data-ttu-id="4137a-111">DefaultStringLength</span><span class="sxs-lookup"><span data-stu-id="4137a-111">DefaultStringLength</span></span>|<span data-ttu-id="4137a-112">この値は、最大の長さが設定されていない文字列の列に対して、既定の長さを指定します。</span><span class="sxs-lookup"><span data-stu-id="4137a-112">This value specifies default length for string columns that have no max length.</span></span><br /><br /> <span data-ttu-id="4137a-113">**既定値:** 4000</span><span class="sxs-lookup"><span data-stu-id="4137a-113">**Default:** 4000</span></span>|  
|<span data-ttu-id="4137a-114">クエリ</span><span class="sxs-lookup"><span data-stu-id="4137a-114">Query</span></span>|<span data-ttu-id="4137a-115">OData のクエリ パラメーター。</span><span class="sxs-lookup"><span data-stu-id="4137a-115">The OData query parameters.</span></span> <span data-ttu-id="4137a-116">このプロパティは式にすることができ、その結果、実行時に設定することができます。</span><span class="sxs-lookup"><span data-stu-id="4137a-116">This property is expression-able and can be set at runtime.</span></span>|  
|<span data-ttu-id="4137a-117">ResourcePath</span><span class="sxs-lookup"><span data-stu-id="4137a-117">ResourcePath</span></span>|<span data-ttu-id="4137a-118">コレクション名のみを選択する代わりに、完全なリソース パスを指定する必要がある場合は、このプロパティを使用します。</span><span class="sxs-lookup"><span data-stu-id="4137a-118">Use this property when you need to specify a full resource path, rather than just selecting a collection name.</span></span> <span data-ttu-id="4137a-119">このプロパティが使用されるのは、 **UseResourcePath** が True の場合のみです。</span><span class="sxs-lookup"><span data-stu-id="4137a-119">This property is used when **UseResourcePath** is True.</span></span>|  
|<span data-ttu-id="4137a-120">UseResourcePath</span><span class="sxs-lookup"><span data-stu-id="4137a-120">UseResourcePath</span></span>|<span data-ttu-id="4137a-121">True に設定されている場合は、OData のフィードの場所を決定するために、ベース URL に対して **ResourcePath** の値が追加されます。</span><span class="sxs-lookup"><span data-stu-id="4137a-121">When set to True, the **ResourcePath** value is appended to the base URL to determine the OData feed location.</span></span> <span data-ttu-id="4137a-122">FALSE に設定すると、 **CollectionName** の値が使用されます。</span><span class="sxs-lookup"><span data-stu-id="4137a-122">When set to False, the **CollectionName** value is used.</span></span><br /><br /> <span data-ttu-id="4137a-123">**既定値:** False</span><span class="sxs-lookup"><span data-stu-id="4137a-123">**Default:** False</span></span>|  
  
  
