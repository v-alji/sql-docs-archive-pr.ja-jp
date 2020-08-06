---
title: OLE DB プロパティについて | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- OLE DB, properties
- SQL Server Native Client OLE DB provider, properties
- properties [OLE DB]
- property values [SQL Server Native Client]
ms.assetid: 0b36a61e-b542-400d-a3d2-e6f643caf2c6
author: rothja
ms.author: jroth
ms.openlocfilehash: d4eb80ab9c0ab90da11d8580e9a2983455b676bb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87714309"
---
# <a name="about-ole-db-properties"></a><span data-ttu-id="d51bc-102">OLE DB プロパティについて</span><span class="sxs-lookup"><span data-stu-id="d51bc-102">About OLE DB Properties</span></span>
  <span data-ttu-id="d51bc-103">コンシューマーは、プロパティ値を設定することで、特定のオブジェクトの動作を要求します。</span><span class="sxs-lookup"><span data-stu-id="d51bc-103">Consumers set property values to request specific object behavior.</span></span> <span data-ttu-id="d51bc-104">たとえば、プロパティを使用して、行セットによって公開されるインターフェイスを指定します。</span><span class="sxs-lookup"><span data-stu-id="d51bc-104">For example, consumers use properties to specify the interfaces to be exposed by a rowset.</span></span> <span data-ttu-id="d51bc-105">コンシューマーは、プロパティ値を取得して、行セット、セッション、データ ソース オブジェクトなど、オブジェクトの機能を判断します。</span><span class="sxs-lookup"><span data-stu-id="d51bc-105">Consumers get the property values to determine the capabilities of an object, such as a rowset, a session, or a data source object.</span></span>  
  
 <span data-ttu-id="d51bc-106">各プロパティには、値、データ型、説明、および読み取り/書き込み属性があります。また、行セット プロパティの場合は、列単位で適用できるかどうかを示すインジケーターがあります。</span><span class="sxs-lookup"><span data-stu-id="d51bc-106">Each property has a value, type, description, and read/write attribute, and for rowset properties, an indicator of whether it can be applied on a column-by-column basis.</span></span>  
  
 <span data-ttu-id="d51bc-107">プロパティは GUID およびプロパティ ID を表す整数によって識別されます。</span><span class="sxs-lookup"><span data-stu-id="d51bc-107">A property is identified by a GUID and an integer representing the property ID.</span></span> <span data-ttu-id="d51bc-108">プロパティ セットは、同じ GUID を共有するすべてのプロパティのセットです。</span><span class="sxs-lookup"><span data-stu-id="d51bc-108">A property set is a set of all properties that share the same GUID.</span></span> <span data-ttu-id="d51bc-109">定義済みの OLE DB プロパティセットに加えて、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーは、プロバイダー固有のプロパティセットとプロパティを実装します。</span><span class="sxs-lookup"><span data-stu-id="d51bc-109">In addition to the predefined OLE DB property sets, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider implements provider-specific property sets and properties in them.</span></span> <span data-ttu-id="d51bc-110">各プロパティは、1 つ以上のプロパティ グループに属しています。</span><span class="sxs-lookup"><span data-stu-id="d51bc-110">Each property belongs to one or more property groups.</span></span> <span data-ttu-id="d51bc-111">プロパティ グループは、特定のオブジェクトに適用されるすべてのプロパティをグループ化したものです。</span><span class="sxs-lookup"><span data-stu-id="d51bc-111">A property group is the group of all properties that apply to a particular object.</span></span> <span data-ttu-id="d51bc-112">プロパティ グループには、初期化プロパティ グループ、データ ソース プロパティ グループ、セッション プロパティ グループ、行セット プロパティ グループ、テーブル プロパティ グループ、列プロパティ グループなどがあります。</span><span class="sxs-lookup"><span data-stu-id="d51bc-112">Some property groups include the initialization property group, data source property group, session property group, rowset property group, table property group, and column property group.</span></span> <span data-ttu-id="d51bc-113">これらの各プロパティ グループに、プロパティが含まれています。</span><span class="sxs-lookup"><span data-stu-id="d51bc-113">There are properties in each of these property groups.</span></span>  
  
 <span data-ttu-id="d51bc-114">プロパティ値を設定するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="d51bc-114">Setting property values involves:</span></span>  
  
1.  <span data-ttu-id="d51bc-115">値を設定するプロパティを決定します。</span><span class="sxs-lookup"><span data-stu-id="d51bc-115">Determining the properties for which to set values.</span></span>  
  
2.  <span data-ttu-id="d51bc-116">目的のプロパティを含むプロパティ セットを決定します。</span><span class="sxs-lookup"><span data-stu-id="d51bc-116">Determining the property sets that contain the identified properties.</span></span>  
  
3.  <span data-ttu-id="d51bc-117">目的のプロパティ セットごとに 1 つ、DBPROPSET 構造体の配列を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="d51bc-117">Allocating an array of DBPROPSET structures, one for each identified property set.</span></span>  
  
4.  <span data-ttu-id="d51bc-118">プロパティ セットごとに DBPROP 構造体の配列を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="d51bc-118">Allocating an array of DBPROP structures for each property set.</span></span> <span data-ttu-id="d51bc-119">各配列の要素数は、そのプロパティ セットに属するプロパティ (手順 1. で特定したプロパティ) の個数です。</span><span class="sxs-lookup"><span data-stu-id="d51bc-119">The number of elements in each array is the number of properties (identified in Step 1) that belong to that property set.</span></span>  
  
5.  <span data-ttu-id="d51bc-120">プロパティごとに DBPROP 構造体に値を設定します。</span><span class="sxs-lookup"><span data-stu-id="d51bc-120">Filling in the DBPROP structure for each property.</span></span>  
  
6.  <span data-ttu-id="d51bc-121">プロパティ セットごとに DBPROPSET 構造体に情報 (プロパティ セット GUID、要素数、および対応する DBPROP 配列を指すポインター) を設定します。</span><span class="sxs-lookup"><span data-stu-id="d51bc-121">Filling in information (property set GUID, count of number of elements, and a pointer to the corresponding DBPROP array) in the DBPROPSET structure for each property set.</span></span>  
  
7.  <span data-ttu-id="d51bc-122">要素数と DBPROPSET 構造体の配列を渡してメソッドを呼び出し、プロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="d51bc-122">Calling a method to set properties and passing the count and the array of DBPROPSET structures.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d51bc-123">参照</span><span class="sxs-lookup"><span data-stu-id="d51bc-123">See Also</span></span>  
 <span data-ttu-id="d51bc-124">[SQL Server Native Client OLE DB プロバイダーアプリケーションの作成](creating-a-sql-server-native-client-ole-db-provider-application.md) </span><span class="sxs-lookup"><span data-stu-id="d51bc-124">[Creating a SQL Server Native Client OLE DB Provider Application](creating-a-sql-server-native-client-ole-db-provider-application.md) </span></span>  
 <span data-ttu-id="d51bc-125">[プロパティ [OLE DB]](https://go.microsoft.com/fwlink/?LinkId=112207)</span><span class="sxs-lookup"><span data-stu-id="d51bc-125">[Properties (OLE DB)](https://go.microsoft.com/fwlink/?LinkId=112207)</span></span>  
  
  
