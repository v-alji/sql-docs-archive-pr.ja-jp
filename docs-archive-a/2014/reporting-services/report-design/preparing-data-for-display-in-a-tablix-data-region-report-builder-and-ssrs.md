---
title: Tablix データ領域に表示するデータの準備 (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: fbb00dc6-7887-480c-b771-cab6fecb8dcc
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 72ac150f2dcd227b1e3afb624a5ca5866fb4c360
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644316"
---
# <a name="preparing-data-for-display-in-a-tablix-data-region-report-builder-and-ssrs"></a><span data-ttu-id="8d918-102">Tablix データ領域に表示するデータの準備 (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="8d918-102">Preparing Data for Display in a Tablix Data Region (Report Builder and SSRS)</span></span>
  <span data-ttu-id="8d918-103">Tablix データ領域には、データセットのデータが表示されます。</span><span class="sxs-lookup"><span data-stu-id="8d918-103">A tablix data region displays data from a dataset.</span></span> <span data-ttu-id="8d918-104">データセットに取得されたすべてのデータを表示することも、フィルターを作成してデータのサブセットのみを表示することもできます。</span><span class="sxs-lookup"><span data-stu-id="8d918-104">You can view all the data retrieved for the dataset or you can create filters so that you see only a subset of the data.</span></span> <span data-ttu-id="8d918-105">NULL 値に入力する条件式を追加したり、データセットのクエリを変更して既存の列の並べ替え順序を定義する列を含めることもできます。</span><span class="sxs-lookup"><span data-stu-id="8d918-105">You can also add conditional expressions to fill in null values or modify the query for a dataset to include columns that define the sort order for an existing column.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="working-with-nulls-and-blanks-in-field-values"></a><span data-ttu-id="8d918-106">NULL および空白のフィールド値の操作</span><span class="sxs-lookup"><span data-stu-id="8d918-106">Working with Nulls and Blanks in Field Values</span></span>  
 <span data-ttu-id="8d918-107">データセット内のフィールド コレクションのデータには、実行時にデータ ソースから取得されたすべてのデータが含まれます。これには、NULL 値と空白の値も含まれます。</span><span class="sxs-lookup"><span data-stu-id="8d918-107">Data for the field collection in a dataset includes all values retrieved from the data source at run time, including null values and blanks.</span></span> <span data-ttu-id="8d918-108">通常、NULL 値と空白の値は区別できませんが、</span><span class="sxs-lookup"><span data-stu-id="8d918-108">Normally null values and blanks are indistinguishable.</span></span> <span data-ttu-id="8d918-109">ほとんどの場合、この動作は適切です。</span><span class="sxs-lookup"><span data-stu-id="8d918-109">In most cases, this is the desired behavior.</span></span> <span data-ttu-id="8d918-110">たとえば、 [Sum](report-builder-functions-sum-function.md) や [Avg](report-builder-functions-avg-function.md) などの数値の集計関数では、NULL 値は無視されます。</span><span class="sxs-lookup"><span data-stu-id="8d918-110">For example, Numeric aggregate functions like [Sum](report-builder-functions-sum-function.md) and [Avg](report-builder-functions-avg-function.md) ignore null values.</span></span> <span data-ttu-id="8d918-111">詳細については、「 [集計関数リファレンス (レポート ビルダーおよび SSRS)](report-builder-functions-aggregate-functions-reference.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8d918-111">For more information, see [Aggregate Functions Reference &#40;Report Builder and SSRS&#41;](report-builder-functions-aggregate-functions-reference.md).</span></span>  
  
 <span data-ttu-id="8d918-112">NULL 値を他の方法で処理する場合は、条件式またはカスタム コードを使用して、NULL 値をカスタム値で置き換えます。</span><span class="sxs-lookup"><span data-stu-id="8d918-112">If you do want to handle null values differently, you can use conditional expressions or custom code to substitute a custom value for the null value.</span></span> <span data-ttu-id="8d918-113">たとえば、次の式は、フィールド `Null` に NULL 値がある場合にテキスト `[Size]`に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="8d918-113">For example, the following expression substitutes the text `Null` wherever a null value occurs in the field `[Size]`.</span></span>  
  
```  
=IIF(Fields!Size.Value IS NOTHING,"Null",Fields!Size.Value)  
```  
  
 <span data-ttu-id="8d918-114">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] クエリを使用して [!INCLUDE[tsql](../../includes/tsql-md.md)] データ ソースからデータを取得する前にデータから NULL 値を削除する方法の詳細については、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SQL Server オンライン ブック [にある](https://go.microsoft.com/fwlink/?linkid=120955)のマニュアルの「NULL 値」および「NULL 値と結合」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8d918-114">For more information about eliminating nulls in your data before retrieving the data from a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data source using [!INCLUDE[tsql](../../includes/tsql-md.md)] queries, see "Null Values" and "Null Values and Joins" in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] documentation in [SQL Server Books Online](https://go.microsoft.com/fwlink/?linkid=120955).</span></span>  
  
## <a name="handling-null-field-names"></a><span data-ttu-id="8d918-115">NULL フィールド名の処理</span><span class="sxs-lookup"><span data-stu-id="8d918-115">Handling Null Field Names</span></span>  
 <span data-ttu-id="8d918-116">フィールド自体がクエリ結果セット内に存在していれば、式で NULL 値のテストを行うことに問題はありません。</span><span class="sxs-lookup"><span data-stu-id="8d918-116">Testing for null values in an expression is fine as long as the field itself exists in the query result set.</span></span> <span data-ttu-id="8d918-117">カスタム コードを使用して、実行時にデータ ソースから返されるコレクション フィールドにフィールド自体が存在するかどうかをテストできます。</span><span class="sxs-lookup"><span data-stu-id="8d918-117">From custom code, you can test whether the field itself is present in the collection fields returned from the data source at run time.</span></span> <span data-ttu-id="8d918-118">詳細については、「[データセット フィールド コレクションの参照 &#40;レポート ビルダーおよび SSRS&#41;](built-in-collections-dataset-fields-collection-references-report-builder.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8d918-118">For more information, see [Dataset Fields Collection References &#40;Report Builder and SSRS&#41;](built-in-collections-dataset-fields-collection-references-report-builder.md).</span></span>  
  
## <a name="adding-a-sort-order-column"></a><span data-ttu-id="8d918-119">[並べ替え順序] 列の追加</span><span class="sxs-lookup"><span data-stu-id="8d918-119">Adding a Sort Order Column</span></span>  
 <span data-ttu-id="8d918-120">既定では、データセット フィールドの値をアルファベット順に並べ替えることができます。</span><span class="sxs-lookup"><span data-stu-id="8d918-120">By default, you can alphabetically sort values in a dataset field.</span></span> <span data-ttu-id="8d918-121">別の順序で並べ替えるには、データ領域で目的の並べ替え順序を定義する新しい列をデータセットに追加します。</span><span class="sxs-lookup"><span data-stu-id="8d918-121">To sort in a different order, you can add a new column to your dataset that defines the sort order you want in a data region.</span></span> <span data-ttu-id="8d918-122">たとえば、フィールド `[Color]` を並べ替えて、白と黒のアイテムを最初に表示するには、次のクエリのように、列 `[ColorSortOrder]`を追加します。</span><span class="sxs-lookup"><span data-stu-id="8d918-122">For example, to sort on the field `[Color]` and sort white and black items first, you can add a column `[ColorSortOrder]`, shown in the following query:</span></span>  
  
```  
SELECT ProductID, p.Name, Color,  
   CASE  
      WHEN p.Color = 'White' THEN 1  
      WHEN p.Color = 'Black' THEN 2  
      WHEN p.Color = 'Blue' THEN 3  
      WHEN p.Color = 'Yellow' THEN 4  
      ELSE 5  
   END As ColorSortOrder  
FROM Production.Product p  
```  
  
 <span data-ttu-id="8d918-123">この並べ替え順序に従ってテーブル データ領域を並べ替えるには、詳細グループの並べ替え式を `=Fields!ColorSortOrder.Value`に設定します。</span><span class="sxs-lookup"><span data-stu-id="8d918-123">To sort a table data region according to this sort order, set the sort expression on the detail group to `=Fields!ColorSortOrder.Value`.</span></span> <span data-ttu-id="8d918-124">詳細については、「[データ領域内のデータの並べ替え &#40;レポート ビルダーおよび SSRS&#41;](sort-data-in-a-data-region-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8d918-124">For more information, see [Sort Data in a Data Region &#40;Report Builder and SSRS&#41;](sort-data-in-a-data-region-report-builder-and-ssrs.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d918-125">参照</span><span class="sxs-lookup"><span data-stu-id="8d918-125">See Also</span></span>  
 <span data-ttu-id="8d918-126">[データセット フィールド コレクション &#40;レポート ビルダーおよび SSRS&#41;](../report-data/dataset-fields-collection-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="8d918-126">[Dataset Fields Collection &#40;Report Builder and SSRS&#41;](../report-data/dataset-fields-collection-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="8d918-127">[式 &#40;レポート ビルダーおよび SSRS&#41;](expressions-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="8d918-127">[Expressions &#40;Report Builder and SSRS&#41;](expressions-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="8d918-128">データのフィルター、グループ化、および並べ替え &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="8d918-128">Filter, Group, and Sort Data &#40;Report Builder and SSRS&#41;</span></span>](filter-group-and-sort-data-report-builder-and-ssrs.md)  
  
  
