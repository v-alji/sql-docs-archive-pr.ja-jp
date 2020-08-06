---
title: ISSCommandWithParameters (OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- ISSCommandWithParameters (OLE DB)
topic_type:
- apiref
helpviewer_keywords:
- ISSCommandWithParameters interface
ms.assetid: 3419b7f3-36a3-4863-816e-e641e4e90496
author: rothja
ms.author: jroth
ms.openlocfilehash: 295026497a97b4ce13d1a1a68de48079809390ad
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634496"
---
# <a name="isscommandwithparameters-ole-db"></a><span data-ttu-id="b9108-102">ISSCommandWithParameters (OLE DB)</span><span class="sxs-lookup"><span data-stu-id="b9108-102">ISSCommandWithParameters (OLE DB)</span></span>
  <span data-ttu-id="b9108-103">**Isscommandwithparameters**は [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 、XML およびユーザー定義型 (UDT) のサポートを公開します。</span><span class="sxs-lookup"><span data-stu-id="b9108-103">**ISSCommandWithParameters** exposes support for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] XML and user-defined types (UDT).</span></span> <span data-ttu-id="b9108-104">これは、コア OLE DB インターフェイス**ICommandWithParameters**から継承する省略可能なインターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="b9108-104">This is an optional interface that inherits from the core OLE DB interface **ICommandWithParameters**.</span></span> <span data-ttu-id="b9108-105">**ICommandWithParameters**から継承された3つのメソッドに加えて、**Getparameterinfo**、 **Mapparameternames**、および**setparameterinfo**;**Isscommandwithparameters**には、サーバー固有のデータ型を処理するために使用される2つの新しいメソッドが用意されています。</span><span class="sxs-lookup"><span data-stu-id="b9108-105">In addition to the three methods inherited from **ICommandWithParameters**; **GetParameterInfo**, **MapParameterNames**, and **SetParameterInfo**; **ISSCommandWithParameters** provides two new methods that are used to handle server specific data types.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b9108-106">**Isscommandwithparameters**インターフェイスは、サービスコンポーネントが使用されている場合に使用できますが、サービスコンポーネント自体はこのインターフェイスを使用しません。</span><span class="sxs-lookup"><span data-stu-id="b9108-106">The **ISSCommandWithParameters** interface can be used when Service Components are used, but the Service Components themselves will not use this interface.</span></span>  
  
|<span data-ttu-id="b9108-107">メソッド</span><span class="sxs-lookup"><span data-stu-id="b9108-107">Method</span></span>|<span data-ttu-id="b9108-108">説明</span><span class="sxs-lookup"><span data-stu-id="b9108-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b9108-109">ISSCommandWithParameters::GetParameterProperties &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="b9108-109">ISSCommandWithParameters::GetParameterProperties &#40;OLE DB&#41;</span></span>](isscommandwithparameters-getparameterproperties-ole-db.md)|<span data-ttu-id="b9108-110">コマンドに渡された各 UDT パラメーターまたは XML パラメーターごとに、1 つの **SSPARAMPROPS** プロパティ セット構造体を返します。他の型のパラメーターの場合、戻り値はありません。</span><span class="sxs-lookup"><span data-stu-id="b9108-110">Returns one **SSPARAMPROPS** property set structure in the array for each UDT or XML parameter passed to the command, but none is returned for other types of parameters.</span></span>|  
|[<span data-ttu-id="b9108-111">ISSCommandWithParameters::SetParameterProperties &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="b9108-111">ISSCommandWithParameters::SetParameterProperties &#40;OLE DB&#41;</span></span>](isscommandwithparameters-setparameterproperties-ole-db.md)|<span data-ttu-id="b9108-112">序数に基づいてパラメーターごとにパラメーターのプロパティを設定するか、または**Ssparc Amprops**構造体の配列を指定して一括パラメータープロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="b9108-112">Sets the parameter properties on a per parameter basis by ordinal, or sets bulk parameter properties by specifying an array of **SSPARAMPROPS** structures.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b9108-113">参照</span><span class="sxs-lookup"><span data-stu-id="b9108-113">See Also</span></span>  
 <span data-ttu-id="b9108-114">[インターフェイス &#40;OLE DB&#41;](../../database-engine/dev-guide/interfaces-ole-db.md) </span><span class="sxs-lookup"><span data-stu-id="b9108-114">[Interfaces &#40;OLE DB&#41;](../../database-engine/dev-guide/interfaces-ole-db.md) </span></span>  
 <span data-ttu-id="b9108-115">[XML データ型の使用](../native-client/features/using-xml-data-types.md) </span><span class="sxs-lookup"><span data-stu-id="b9108-115">[Using XML Data Types](../native-client/features/using-xml-data-types.md) </span></span>  
 [<span data-ttu-id="b9108-116">ユーザー定義型の使用</span><span class="sxs-lookup"><span data-stu-id="b9108-116">Using User-Defined Types</span></span>](../native-client/features/using-user-defined-types.md)  
  
  
