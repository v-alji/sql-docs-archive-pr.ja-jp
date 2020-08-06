---
title: DataReader 変換先のカスタム プロパティ | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: f151c3e8-3811-457d-a3d3-6158ca65a646
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 62b6f628614d533e1bebcce071ce4761e73e08f7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641782"
---
# <a name="datareader-destination-custom-properties"></a><span data-ttu-id="201ed-102">DataReader 変換先のカスタム プロパティ</span><span class="sxs-lookup"><span data-stu-id="201ed-102">DataReader Destination Custom Properties</span></span>
  <span data-ttu-id="201ed-103">DataReader 変換先には、カスタム プロパティと、すべてのデータ フロー コンポーネントとの共通プロパティの両方があります。</span><span class="sxs-lookup"><span data-stu-id="201ed-103">The DataReader destination has both custom properties and the properties common to all data flow components.</span></span>  
  
 <span data-ttu-id="201ed-104">次の表は、DataReader 変換先のカスタム プロパティを示しています。</span><span class="sxs-lookup"><span data-stu-id="201ed-104">The following table describes the custom properties of the DataReader destination.</span></span> <span data-ttu-id="201ed-105">`DataReader` を除き、すべてのプロパティは読み取り/書き込み可能です。</span><span class="sxs-lookup"><span data-stu-id="201ed-105">All properties except for `DataReader` are read/write.</span></span>  
  
|<span data-ttu-id="201ed-106">プロパティ名</span><span class="sxs-lookup"><span data-stu-id="201ed-106">Property name</span></span>|<span data-ttu-id="201ed-107">データ型</span><span class="sxs-lookup"><span data-stu-id="201ed-107">Data Type</span></span>|<span data-ttu-id="201ed-108">説明</span><span class="sxs-lookup"><span data-stu-id="201ed-108">Description</span></span>|  
|-------------------|---------------|-----------------|  
|<span data-ttu-id="201ed-109">DataReader</span><span class="sxs-lookup"><span data-stu-id="201ed-109">DataReader</span></span>|<span data-ttu-id="201ed-110">String</span><span class="sxs-lookup"><span data-stu-id="201ed-110">String</span></span>|<span data-ttu-id="201ed-111">DataReader 変換先のクラス名。</span><span class="sxs-lookup"><span data-stu-id="201ed-111">The class name of the DataReader destination.</span></span>|  
|<span data-ttu-id="201ed-112">FailOnTimeout</span><span class="sxs-lookup"><span data-stu-id="201ed-112">FailOnTimeout</span></span>|<span data-ttu-id="201ed-113">Boolean</span><span class="sxs-lookup"><span data-stu-id="201ed-113">Boolean</span></span>|<span data-ttu-id="201ed-114">`ReadTimeout` が発生したときに失敗するかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="201ed-114">Indicates whether to fail when a `ReadTimeout` occurs.</span></span> <span data-ttu-id="201ed-115">このプロパティの既定値は **False**です。</span><span class="sxs-lookup"><span data-stu-id="201ed-115">The default value of this property is **False**.</span></span>|  
|<span data-ttu-id="201ed-116">ReadTimeout</span><span class="sxs-lookup"><span data-stu-id="201ed-116">ReadTimeout</span></span>|<span data-ttu-id="201ed-117">整数</span><span class="sxs-lookup"><span data-stu-id="201ed-117">Integer</span></span>|<span data-ttu-id="201ed-118">タイムアウトが発生するまでの時間 (ミリ秒単位)。</span><span class="sxs-lookup"><span data-stu-id="201ed-118">The number of milliseconds before a time-out occurs.</span></span> <span data-ttu-id="201ed-119">このプロパティの既定値は 30000 (30 秒) です。</span><span class="sxs-lookup"><span data-stu-id="201ed-119">The default value of this property is 30000 (30 seconds).</span></span>|  
  
 <span data-ttu-id="201ed-120">DataReader 変換先の入力および入力列には、カスタム プロパティはありません。</span><span class="sxs-lookup"><span data-stu-id="201ed-120">The input and the input columns of the DataReader destination have no custom properties.</span></span>  
  
 <span data-ttu-id="201ed-121">詳細については、「 [DataReader 変換先](datareader-destination.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="201ed-121">For more information, see [DataReader Destination](datareader-destination.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="201ed-122">参照</span><span class="sxs-lookup"><span data-stu-id="201ed-122">See Also</span></span>  
 [<span data-ttu-id="201ed-123">Common Properties</span><span class="sxs-lookup"><span data-stu-id="201ed-123">Common Properties</span></span>](../common-properties.md)  
  
  
