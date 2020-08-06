---
title: レベルのプロパティ |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- user hierarchies [Analysis Services]
- hierarchies [Analysis Services], user
ms.assetid: dabb7335-887b-442a-b67c-4901ba1242b7
author: minewiskan
ms.author: owend
ms.openlocfilehash: 553503b9d35142bcc998b4ec12ad2e29d4c66318
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632763"
---
# <a name="level-properties"></a><span data-ttu-id="1dbb9-102">レベル プロパティ</span><span class="sxs-lookup"><span data-stu-id="1dbb9-102">Level Properties</span></span> 
  <span data-ttu-id="1dbb9-103">次の表では、ユーザー定義階層におけるレベルのプロパティの一覧および説明を示します。</span><span class="sxs-lookup"><span data-stu-id="1dbb9-103">The following table lists and describes the properties of a level in a user-defined hierarchy.</span></span>  
  
|<span data-ttu-id="1dbb9-104">プロパティ</span><span class="sxs-lookup"><span data-stu-id="1dbb9-104">Property</span></span>|<span data-ttu-id="1dbb9-105">説明</span><span class="sxs-lookup"><span data-stu-id="1dbb9-105">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="1dbb9-106">説明</span><span class="sxs-lookup"><span data-stu-id="1dbb9-106">Description</span></span>|<span data-ttu-id="1dbb9-107">レベルの説明を格納します。</span><span class="sxs-lookup"><span data-stu-id="1dbb9-107">Contains the description of the level.</span></span>|  
|<span data-ttu-id="1dbb9-108">HideMemberIf</span><span class="sxs-lookup"><span data-stu-id="1dbb9-108">HideMemberIf</span></span>|<span data-ttu-id="1dbb9-109">レベル内のメンバーをクライアント アプリケーションに対して非表示にするかどうかと、そのタイミングを示します。</span><span class="sxs-lookup"><span data-stu-id="1dbb9-109">Indicates whether and when a member in a level should be hidden from client applications.</span></span> <span data-ttu-id="1dbb9-110">このプロパティは、以下の値をとります。</span><span class="sxs-lookup"><span data-stu-id="1dbb9-110">This property can have the following values:</span></span><br /><br /> <span data-ttu-id="1dbb9-111">行わない</span><span class="sxs-lookup"><span data-stu-id="1dbb9-111">Never</span></span><br /> <span data-ttu-id="1dbb9-112">メンバーは必ず表示されます。</span><span class="sxs-lookup"><span data-stu-id="1dbb9-112">Members are never hidden.</span></span> <span data-ttu-id="1dbb9-113">これが既定値です。</span><span class="sxs-lookup"><span data-stu-id="1dbb9-113">This is the default value.</span></span><br /><br /> <span data-ttu-id="1dbb9-114">OnlyChildWithNoName</span><span class="sxs-lookup"><span data-stu-id="1dbb9-114">OnlyChildWithNoName</span></span><br /> <span data-ttu-id="1dbb9-115">メンバーがその親の唯一の子であり、メンバーの名前が空の場合、メンバーは非表示になります。</span><span class="sxs-lookup"><span data-stu-id="1dbb9-115">A member is hidden when the member is the only child of its parent and the member's name is empty.</span></span><br /><br /> <span data-ttu-id="1dbb9-116">OnlyChildWithParentName</span><span class="sxs-lookup"><span data-stu-id="1dbb9-116">OnlyChildWithParentName</span></span><br /> <span data-ttu-id="1dbb9-117">メンバーがその親の唯一の子で、メンバーの名前が親の名前と同じ場合、メンバーは表示されません。</span><span class="sxs-lookup"><span data-stu-id="1dbb9-117">A member is hidden when the member is the only child of its parent and the member's name is identical to that of its parent.</span></span><br /><br /> <span data-ttu-id="1dbb9-118">NoName</span><span class="sxs-lookup"><span data-stu-id="1dbb9-118">NoName</span></span><br /> <span data-ttu-id="1dbb9-119">メンバーの名前が空の場合、メンバーは表示されません。</span><span class="sxs-lookup"><span data-stu-id="1dbb9-119">A member is hidden when the member's name is empty.</span></span><br /><br /> <span data-ttu-id="1dbb9-120">ParentName</span><span class="sxs-lookup"><span data-stu-id="1dbb9-120">ParentName</span></span><br /> <span data-ttu-id="1dbb9-121">メンバーの名前がその親の名前と同じである場合、メンバーは表示されません。</span><span class="sxs-lookup"><span data-stu-id="1dbb9-121">A member is hidden when the member's name is identical to that of its parent.</span></span>|  
|<span data-ttu-id="1dbb9-122">id</span><span class="sxs-lookup"><span data-stu-id="1dbb9-122">ID</span></span>|<span data-ttu-id="1dbb9-123">レベルの一意の識別子 (ID) を格納します。</span><span class="sxs-lookup"><span data-stu-id="1dbb9-123">Contains the unique identifier (ID) of the level.</span></span>|  
|<span data-ttu-id="1dbb9-124">名前</span><span class="sxs-lookup"><span data-stu-id="1dbb9-124">Name</span></span>|<span data-ttu-id="1dbb9-125">レベルの表示名を格納します。</span><span class="sxs-lookup"><span data-stu-id="1dbb9-125">Contains the friendly name of the level.</span></span> <span data-ttu-id="1dbb9-126">既定では、レベルの名前はソース属性の名前と同じです。</span><span class="sxs-lookup"><span data-stu-id="1dbb9-126">By default, the name of a level is the same as the name of the source attribute.</span></span>|  
|<span data-ttu-id="1dbb9-127">SourceAttribute</span><span class="sxs-lookup"><span data-stu-id="1dbb9-127">SourceAttribute</span></span>|<span data-ttu-id="1dbb9-128">レベルの基になるソース属性の名前を格納します。</span><span class="sxs-lookup"><span data-stu-id="1dbb9-128">Contains the name of the source attribute on which the level is based.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1dbb9-129">参照</span><span class="sxs-lookup"><span data-stu-id="1dbb9-129">See Also</span></span>  
 [<span data-ttu-id="1dbb9-130">ユーザー階層プロパティ</span><span class="sxs-lookup"><span data-stu-id="1dbb9-130">User Hierarchy Properties</span></span>](user-hierarchies-properties.md)  
  
  
