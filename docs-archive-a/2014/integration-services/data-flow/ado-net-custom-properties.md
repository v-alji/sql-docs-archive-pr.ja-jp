---
title: ADO NET カスタム プロパティ | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: e062a9ab-1e6b-4061-845a-4f8a0552b09d
author: chugugrace
ms.author: chugu
ms.openlocfilehash: bada6f512770d0f9f07ddc3693070c8aad309cb5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87712258"
---
# <a name="ado-net-custom-properties"></a><span data-ttu-id="b98d7-102">ADO NET カスタム プロパティ</span><span class="sxs-lookup"><span data-stu-id="b98d7-102">ADO NET Custom Properties</span></span>
  <span data-ttu-id="b98d7-103">**変換元のカスタム プロパティ**</span><span class="sxs-lookup"><span data-stu-id="b98d7-103">**Source Custom Properties**</span></span>  
  
 <span data-ttu-id="b98d7-104">ADO NET ソースには、カスタム プロパティと、すべてのデータ フロー コンポーネントとの共通プロパティの両方があります。</span><span class="sxs-lookup"><span data-stu-id="b98d7-104">The ADO NET source has both custom properties and the properties common to all data flow components.</span></span>  
  
 <span data-ttu-id="b98d7-105">次の表は、ADO NET ソースのカスタム プロパティを示しています。</span><span class="sxs-lookup"><span data-stu-id="b98d7-105">The following table describes the custom properties of the ADO NET source.</span></span> <span data-ttu-id="b98d7-106">すべてのプロパティは読み取り/書き込み可能です。</span><span class="sxs-lookup"><span data-stu-id="b98d7-106">All properties are read/write.</span></span>  
  
|<span data-ttu-id="b98d7-107">プロパティ名</span><span class="sxs-lookup"><span data-stu-id="b98d7-107">Property name</span></span>|<span data-ttu-id="b98d7-108">データ型</span><span class="sxs-lookup"><span data-stu-id="b98d7-108">Data Type</span></span>|<span data-ttu-id="b98d7-109">説明</span><span class="sxs-lookup"><span data-stu-id="b98d7-109">Description</span></span>|  
|-------------------|---------------|-----------------|  
|<span data-ttu-id="b98d7-110">CommandTimeOut</span><span class="sxs-lookup"><span data-stu-id="b98d7-110">CommandTimeout</span></span>|<span data-ttu-id="b98d7-111">String</span><span class="sxs-lookup"><span data-stu-id="b98d7-111">String</span></span>|<span data-ttu-id="b98d7-112">SQL コマンドがタイムアウトになる時間を秒数で指定する値です。値が 0 の場合、コマンドはタイムアウトになりません。</span><span class="sxs-lookup"><span data-stu-id="b98d7-112">A value that specifies the number of seconds before the SQL command times out. A value of 0 indicates that the command never times out.</span></span>|  
|<span data-ttu-id="b98d7-113">SqlCommand</span><span class="sxs-lookup"><span data-stu-id="b98d7-113">SqlCommand</span></span>|<span data-ttu-id="b98d7-114">String</span><span class="sxs-lookup"><span data-stu-id="b98d7-114">String</span></span>|<span data-ttu-id="b98d7-115">ADO NET ソースがデータの抽出に使用する SQL ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="b98d7-115">The SQL statement that the ADO NET source uses to extract data.</span></span><br /><br /> <span data-ttu-id="b98d7-116">パッケージを読み込むときに、ADO NET ソースが使用する SQL ステートメントでこのプロパティを動的に更新できます。</span><span class="sxs-lookup"><span data-stu-id="b98d7-116">When the package loads, you can dynamically update this property with the SQL statement that the ADO NET source will use.</span></span> <span data-ttu-id="b98d7-117">詳しくは、「[Integration Services &#40;SSIS&#41; の式](../expressions/integration-services-ssis-expressions.md)」および「[パッケージでプロパティ式を使用する](../expressions/use-property-expressions-in-packages.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="b98d7-117">For more information, see [Integration Services &#40;SSIS&#41; Expressions](../expressions/integration-services-ssis-expressions.md) and [Use Property Expressions in Packages](../expressions/use-property-expressions-in-packages.md).</span></span>|  
|<span data-ttu-id="b98d7-118">AllowImplicitStringConversion</span><span class="sxs-lookup"><span data-stu-id="b98d7-118">AllowImplicitStringConversion</span></span>|<span data-ttu-id="b98d7-119">Boolean</span><span class="sxs-lookup"><span data-stu-id="b98d7-119">Boolean</span></span>|<span data-ttu-id="b98d7-120">次の処理を実行するかどうかを示す値です。</span><span class="sxs-lookup"><span data-stu-id="b98d7-120">A value that indicates whether the following occurs:</span></span><br /><br /> <span data-ttu-id="b98d7-121">外部メタデータの型と文字列型である出力列の型が一致しない場合に、検証エラーを生成しない (DT_WSTR または DT_NTEXT)。</span><span class="sxs-lookup"><span data-stu-id="b98d7-121">No generation of a validation error if there is a mismatch between external metadata types and output column types that are strings (DT_WSTR or DT_NTEXT).</span></span><br /><br /> <span data-ttu-id="b98d7-122">外部メタデータの型を、出力列が使用する文字列データ型に暗黙的に変換する。</span><span class="sxs-lookup"><span data-stu-id="b98d7-122">Implicit conversion of external metadata types to the string data type that the output column uses.</span></span><br /><br /> <br /><br /> <span data-ttu-id="b98d7-123">既定値は TRUE です。</span><span class="sxs-lookup"><span data-stu-id="b98d7-123">The default value is TRUE.</span></span><br /><br /> <span data-ttu-id="b98d7-124">詳しくは、「 [ADO NET ソース](ado-net-source.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="b98d7-124">For more information, see [ADO NET Source](ado-net-source.md).</span></span>|  
  
 <span data-ttu-id="b98d7-125">ADO NET ソースの出力および出力列には、カスタム プロパティがありません。</span><span class="sxs-lookup"><span data-stu-id="b98d7-125">The output and the output columns of the ADO NET source have no custom properties.</span></span>  
  
 <span data-ttu-id="b98d7-126">詳しくは、「 [ADO NET ソース](ado-net-source.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="b98d7-126">For more information, see [ADO NET Source](ado-net-source.md).</span></span>  
  
 <span data-ttu-id="b98d7-127">**変換先のカスタム プロパティ**</span><span class="sxs-lookup"><span data-stu-id="b98d7-127">**Destination Custom Properties**</span></span>  
  
 <span data-ttu-id="b98d7-128">[!INCLUDE[vstecado](../../includes/vstecado-md.md)] 変換先には、カスタム プロパティと、すべてのデータ フロー コンポーネントに共通するプロパティの両方があります。</span><span class="sxs-lookup"><span data-stu-id="b98d7-128">The [!INCLUDE[vstecado](../../includes/vstecado-md.md)] destination has both custom properties and the properties common to all data flow components.</span></span>  
  
 <span data-ttu-id="b98d7-129">次の表は、 [!INCLUDE[vstecado](../../includes/vstecado-md.md)] 変換先のカスタム プロパティを示しています。</span><span class="sxs-lookup"><span data-stu-id="b98d7-129">The following table describes the custom properties of the [!INCLUDE[vstecado](../../includes/vstecado-md.md)] destination.</span></span> <span data-ttu-id="b98d7-130">すべてのプロパティは読み取り/書き込み可能です。</span><span class="sxs-lookup"><span data-stu-id="b98d7-130">All properties are read/write.</span></span> <span data-ttu-id="b98d7-131">これらのプロパティは、 **[ADO.NET 変換先エディター]** ではアクセスできませんが、 **[詳細エディター]** を使用して設定できます。</span><span class="sxs-lookup"><span data-stu-id="b98d7-131">These properties are not available in the **ADO NET Destination Editor**, but can be set by using the **Advanced Editor**.</span></span>  
  
|<span data-ttu-id="b98d7-132">プロパティ</span><span class="sxs-lookup"><span data-stu-id="b98d7-132">Property</span></span>|<span data-ttu-id="b98d7-133">データ型</span><span class="sxs-lookup"><span data-stu-id="b98d7-133">Data Type</span></span>|<span data-ttu-id="b98d7-134">説明</span><span class="sxs-lookup"><span data-stu-id="b98d7-134">Description</span></span>|  
|--------------|---------------|-----------------|  
|<span data-ttu-id="b98d7-135">BatchSize</span><span class="sxs-lookup"><span data-stu-id="b98d7-135">BatchSize</span></span>|<span data-ttu-id="b98d7-136">Integer</span><span class="sxs-lookup"><span data-stu-id="b98d7-136">Integer</span></span>|<span data-ttu-id="b98d7-137">サーバーに送信されるバッチ内の行数です。</span><span class="sxs-lookup"><span data-stu-id="b98d7-137">The number of rows in a batch that is sent to the server.</span></span> <span data-ttu-id="b98d7-138">値 **0** は、バッチ サイズが内部バッファーのサイズに一致することを示します。</span><span class="sxs-lookup"><span data-stu-id="b98d7-138">A value of **0** indicates that the batch size matches the internal buffer size.</span></span> <span data-ttu-id="b98d7-139">このプロパティの既定値は **0**です。</span><span class="sxs-lookup"><span data-stu-id="b98d7-139">The default value of this property is **0**.</span></span>|  
|<span data-ttu-id="b98d7-140">CommandTimeOut</span><span class="sxs-lookup"><span data-stu-id="b98d7-140">CommandTimeOut</span></span>|<span data-ttu-id="b98d7-141">Integer</span><span class="sxs-lookup"><span data-stu-id="b98d7-141">Integer</span></span>|<span data-ttu-id="b98d7-142">SQL コマンドがタイムアウトになるまでの最大秒数。この値に **0** を指定すると、時間は無制限になります。</span><span class="sxs-lookup"><span data-stu-id="b98d7-142">The maximum number of seconds that the SQL command can run before timing out. A value of **0** indicates an infinite time.</span></span> <span data-ttu-id="b98d7-143">このプロパティの既定値は **0**です。</span><span class="sxs-lookup"><span data-stu-id="b98d7-143">The default value of this property is **0**.</span></span>|  
|<span data-ttu-id="b98d7-144">TableOrViewName</span><span class="sxs-lookup"><span data-stu-id="b98d7-144">TableOrViewName</span></span>|<span data-ttu-id="b98d7-145">String</span><span class="sxs-lookup"><span data-stu-id="b98d7-145">String</span></span>|<span data-ttu-id="b98d7-146">変換先のテーブルまたはビューの名前。</span><span class="sxs-lookup"><span data-stu-id="b98d7-146">The name of the destination table or view.</span></span>|  
  
 <span data-ttu-id="b98d7-147">詳しくは、「 [ADO NET 変換先](ado-net-destination.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="b98d7-147">For more information, see [ADO NET Destination](ado-net-destination.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b98d7-148">参照</span><span class="sxs-lookup"><span data-stu-id="b98d7-148">See Also</span></span>  
 [<span data-ttu-id="b98d7-149">Common Properties</span><span class="sxs-lookup"><span data-stu-id="b98d7-149">Common Properties</span></span>](../common-properties.md)  
  
  
