---
title: 入れ子になったテーブル (Analysis Services データマイニング) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- data mining [Analysis Services], nested tables
- tables [Analysis Services], nested
- nested tables
ms.assetid: cb192aa2-597e-4d4f-ac34-3556d037fed4
author: minewiskan
ms.author: owend
ms.openlocfilehash: 78b1022751ae6d381b86512f45f7232bebe7fcd0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87712642"
---
# <a name="nested-tables-analysis-services---data-mining"></a><span data-ttu-id="0fc80-102">入れ子になったテーブル (Analysis Services - データ マイニング)</span><span class="sxs-lookup"><span data-stu-id="0fc80-102">Nested Tables (Analysis Services - Data Mining)</span></span>
  <span data-ttu-id="0fc80-103">では [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 、データをケーステーブル内に含まれる一連のケースとしてデータマイニングアルゴリズムに渡す必要があります。</span><span class="sxs-lookup"><span data-stu-id="0fc80-103">In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], data must be fed to a data mining algorithm as a series of cases that are contained within a case table.</span></span> <span data-ttu-id="0fc80-104">しかし、1 行のデータですべてのケースを表すことはできません。</span><span class="sxs-lookup"><span data-stu-id="0fc80-104">However, not all cases can be described by a single row of data.</span></span> <span data-ttu-id="0fc80-105">たとえば、1 つのテーブルに顧客情報、別のテーブルに顧客の購入記録が含まれている 2 つのテーブルから、ケースが派生している場合があります。</span><span class="sxs-lookup"><span data-stu-id="0fc80-105">For example, a case might be derived from two tables: one table that contains customer information, and another table that contains customer purchases.</span></span> <span data-ttu-id="0fc80-106">顧客情報テーブルの 1 人の顧客が顧客購入記録テーブルに複数の項目を持っている場合、1 行でデータを表すことが難しくなります。</span><span class="sxs-lookup"><span data-stu-id="0fc80-106">A single customer in the customer information table might have multiple items in the customer purchases table, which makes it difficult to describe the data by using a single row.</span></span> [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]<span data-ttu-id="0fc80-107">*入れ子になったテーブル*を使用して、これらのケースを処理するための一意の方法を提供します。</span><span class="sxs-lookup"><span data-stu-id="0fc80-107">provides a unique method for handling these cases, by using *nested tables*.</span></span> <span data-ttu-id="0fc80-108">次の図は、入れ子になったテーブルの概念を示しています。</span><span class="sxs-lookup"><span data-stu-id="0fc80-108">The concept of a nested table is demonstrated in the following illustration.</span></span>  
  
 <span data-ttu-id="0fc80-109">![入れ子になったテーブルを使用して結合された 2 つのテーブル](../media/nested-tables.gif "入れ子になったテーブルを使用して結合された 2 つのテーブル")</span><span class="sxs-lookup"><span data-stu-id="0fc80-109">![Two tables combined by using a nested table](../media/nested-tables.gif "Two tables combined by using a nested table")</span></span>  
  
 <span data-ttu-id="0fc80-110">この図では、親テーブルである最初のテーブルに顧客に関する情報が含まれ、各顧客の一意の識別子が付けられています。</span><span class="sxs-lookup"><span data-stu-id="0fc80-110">In this diagram, the first table, which is the parent table, contains information about customers, and associates a unique identifier for each customer.</span></span> <span data-ttu-id="0fc80-111">子テーブルである 2 番目のテーブルには、各顧客の購入記録が含まれています。</span><span class="sxs-lookup"><span data-stu-id="0fc80-111">The second table, the child table, contains the purchases for each customer.</span></span> <span data-ttu-id="0fc80-112">子テーブルの購入記録は、一意の識別子である **CustomerKey** 列によって親テーブルに関連付けられています。</span><span class="sxs-lookup"><span data-stu-id="0fc80-112">The purchases in the child table are related to the parent table by the unique identifier, the **CustomerKey** column.</span></span> <span data-ttu-id="0fc80-113">図の 3 番目のテーブルは、2 つのテーブルが結合されていることを示します。</span><span class="sxs-lookup"><span data-stu-id="0fc80-113">The third table in the diagram shows the two tables combined.</span></span>  
  
 <span data-ttu-id="0fc80-114">入れ子になったテーブルは、ケース テーブル内で **TABLE**のデータ型を持つ特別な列として表されます。</span><span class="sxs-lookup"><span data-stu-id="0fc80-114">A nested table is represented in the case table as a special column that has a data type of **TABLE**.</span></span> <span data-ttu-id="0fc80-115">特定のケース行では、この種類の列に、親テーブルに関係する子テーブルから選択された列が含まれます。</span><span class="sxs-lookup"><span data-stu-id="0fc80-115">For any particular case row, this kind of column contains selected rows from the child table that pertain to the parent table.</span></span>  
  
 <span data-ttu-id="0fc80-116">入れ子になったテーブルのデータを、予測または入力、あるいは予測と入力の両方に使用できます。</span><span class="sxs-lookup"><span data-stu-id="0fc80-116">The data in a nested table can be used for prediction or for input, or for both.</span></span> <span data-ttu-id="0fc80-117">たとえば、モデルに 2 つの入れ子になったテーブル列が含まれているとします。1 つの列には顧客が購入した製品の一覧が含まれ、もう 1 つの列には、アンケートから収集された顧客の趣味や関心に関する情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="0fc80-117">For example, you might have two nested table columns in a model: one nested table column might contain a list of the products that a customer has purchased, while the other nested table column contains information about the customer's hobbies and interests, possibly obtained from a survey.</span></span> <span data-ttu-id="0fc80-118">この場合、顧客の趣味や関心を、購入行動を分析する入力として使用し、購入の可能性がある製品を予測できます。</span><span class="sxs-lookup"><span data-stu-id="0fc80-118">In this scenario, you could use the customer's hobbies and interests as an input for analyzing purchasing behavior, and predicting likely purchases.</span></span>  
  
## <a name="joining-case-tables-and-nested-tables"></a><span data-ttu-id="0fc80-119">ケース テーブルと入れ子になったテーブルの結合</span><span class="sxs-lookup"><span data-stu-id="0fc80-119">Joining Case Tables and Nested Tables</span></span>  
 <span data-ttu-id="0fc80-120">入れ子になったテーブルを作成するには、一方のテーブル内の項目を他方のテーブルに関連付けできるように、2 つのソース テーブルに定義済みのリレーションシップを含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="0fc80-120">In order to create a nested table, the two source tables must contain a defined relationship so that the items in one table can be related to the other table.</span></span> <span data-ttu-id="0fc80-121">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]では、データ ソース ビュー内でこのリレーションシップを定義できます。</span><span class="sxs-lookup"><span data-stu-id="0fc80-121">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], you can define this relationship in the data source view.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0fc80-122">**CustomerKey** フィールドはリレーショナル キーです。リレーショナル キーは、データ ソース ビュー定義内でケース テーブルと入れ子になったテーブルを関連付けたり、マイニング構造内で列のリレーションシップを確立したりするために使用されます。</span><span class="sxs-lookup"><span data-stu-id="0fc80-122">The **CustomerKey** field is the relational key that is used to link the case table and the nested table within the data source view definition, and to establish the relationship of the columns within the mining structure.</span></span> <span data-ttu-id="0fc80-123">ただし、このリレーショナル キーは、その構造に基づいて作成されるマイニング モデルでは通常は使用されません。</span><span class="sxs-lookup"><span data-stu-id="0fc80-123">However, typically you should not use this relational key in mining models built on that structure.</span></span> <span data-ttu-id="0fc80-124">一般に、リレーショナル キー列がテーブルを結合するためだけに使用されていて、分析に関係する情報は何も提供していない場合は、マイニング モデルではそのリレーショナル キー列を省略することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="0fc80-124">Usually it is best to omit the relational key column from the mining model if it serves only to join the tables and does not provide information that is interesting for analysis.</span></span>  
  
 <span data-ttu-id="0fc80-125">データ マイニング拡張機能 (DMX) または分析管理オブジェクト (AMO) を使用して、入れ子になったテーブルをプログラムによって作成できます。または、 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]のデータ マイニング ウィザードおよびデータ マイニング デザイナーを使用できます。</span><span class="sxs-lookup"><span data-stu-id="0fc80-125">You can create nested tables programmatically by either using Data Mining Extensions (DMX) or Analysis Management Objects (AMO), or you can use the Data Mining Wizard and Data Mining Designer in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].</span></span>  
  
## <a name="using-nested-table-columns-in-a-mining-model"></a><span data-ttu-id="0fc80-126">マイニング モデルでの入れ子になったテーブル列の使用</span><span class="sxs-lookup"><span data-stu-id="0fc80-126">Using Nested Table Columns in a Mining Model</span></span>  
 <span data-ttu-id="0fc80-127">ケース テーブルのキーは多くの場合、顧客 ID、製品名、連続する日付など、テーブルの行を一意に識別するデータです。</span><span class="sxs-lookup"><span data-stu-id="0fc80-127">In the case table, the key is often a customer ID, a product name, or date in a series: data that uniquely identifies a row in the table.</span></span> <span data-ttu-id="0fc80-128">.</span><span class="sxs-lookup"><span data-stu-id="0fc80-128">.</span></span> <span data-ttu-id="0fc80-129">しかし、入れ子になったテーブルのキーは、そのリレーショナル キー (外部キー) ではなく、モデル化する属性を表す列であるのが一般的です。</span><span class="sxs-lookup"><span data-stu-id="0fc80-129">However, in nested tables, the key is typically not the relational key (or foreign key) but rather the column that represents the attribute that you are modeling.</span></span>  
  
 <span data-ttu-id="0fc80-130">たとえば、ケース テーブルに注文が含まれていて、入れ子になったテーブルに注文の品目が含まれている場合、入れ子になったテーブルに格納されている品目間の関係を (ケース テーブルに格納されている) 複数の注文にまたがってモデル化することも考えられます。</span><span class="sxs-lookup"><span data-stu-id="0fc80-130">For example, if the case table contains orders, and the nested table contains items in the order, you would be interested in modeling the relationship between items stored in the nested table across multiple orders, which are stored in the case table.</span></span> <span data-ttu-id="0fc80-131">したがって、入れ子になったテーブル **Items** がケース テーブル **Orders** にリレーショナル キー **OrderID**で結合されていても、 **OrderID** を入れ子になったテーブルのキーとして使用するべきではありません。</span><span class="sxs-lookup"><span data-stu-id="0fc80-131">Therefore, although the **Items** nested table is joined to the **Orders** case table by the relational key **OrderID**, you should not use **OrderID** as the nested table key.</span></span> <span data-ttu-id="0fc80-132">この場合は、モデル化するデータが **Items** 列に含まれているため、代わりにその列を入れ子になったテーブルのキーとして選択します。</span><span class="sxs-lookup"><span data-stu-id="0fc80-132">Instead, you would select the **Items** column as the nested table key, because that column contains the data that you want to model.</span></span> <span data-ttu-id="0fc80-133">ケース テーブルと入れ子になったテーブルの間のリレーションシップはデータ ソース ビュー定義によって既に確立されているため、ほとんどの場合、マイニング モデルで **OrderID** を無視しても問題にはなりません。</span><span class="sxs-lookup"><span data-stu-id="0fc80-133">In most cases, you can safely ignore **OrderID** in the mining model, because the relationship between the case table and the nested table has already been established by the data source view definition.</span></span>  
  
 <span data-ttu-id="0fc80-134">入れ子になったテーブルのキーとして使用する列を選択するときには、その列の値が各ケースで一意であることを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0fc80-134">When you choose a column to use as the nested table key, you must ensure that the values in that column are unique for each case.</span></span> <span data-ttu-id="0fc80-135">たとえば、ケース テーブルが顧客を表し、入れ子になったテーブルが顧客が購入した品目を表す場合は、各顧客について複数回登録されている品目がないことを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0fc80-135">For example, if the case table represents customers and the nested table represents items purchased by the customer, you must ensure that no item is listed more than one time per customer.</span></span> <span data-ttu-id="0fc80-136">顧客が同じ品目を複数回購入している場合は、一意の各製品の購入回数を集計する列を含む別のビューを作成することができます。</span><span class="sxs-lookup"><span data-stu-id="0fc80-136">If a customer has purchased the same item more than one time, you might want to create a different view that has a column that aggregates the count of purchases for each unique product.</span></span>  
  
 <span data-ttu-id="0fc80-137">入れ子になったテーブルの値の重複をどのように処理するかは、作成するマイニング モデルや解決するビジネス上の問題によって異なります。</span><span class="sxs-lookup"><span data-stu-id="0fc80-137">How you decide to handle duplicate values in a nested table depends on the mining model that you are creating and the business problem that you are solving.</span></span> <span data-ttu-id="0fc80-138">たとえば、顧客が特定の製品を購入した回数は問題にならず、少なくとも 1 回購入しているかどうかさえわかればよい場合もあれば、</span><span class="sxs-lookup"><span data-stu-id="0fc80-138">In some scenarios you might not care how many times a customer has purchased a particular product, but want to check for the existence of at least one purchase.</span></span> <span data-ttu-id="0fc80-139">購入の数量と順序が重要になる場合もあります。</span><span class="sxs-lookup"><span data-stu-id="0fc80-139">In other scenarios, the quantity and sequence of purchases might be very important.</span></span>  
  
 <span data-ttu-id="0fc80-140">品目の順序が重要な場合は、順序を示す追加の列が必要になることもあります。</span><span class="sxs-lookup"><span data-stu-id="0fc80-140">If the order of items is important, you might need an additional column that indicates the sequence.</span></span> <span data-ttu-id="0fc80-141">シーケンス クラスター アルゴリズムを使用してモデルを作成する際には、品目の順序を表す追加の *key sequence* 列を選択する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0fc80-141">When you use the sequence clustering algorithm to create a model, you must choose an additional *key sequence* column to represent the order of the items.</span></span> <span data-ttu-id="0fc80-142">key sequence 列は、シーケンス クラスター モデルだけで使用される特別な種類の入れ子になったキーで、一意の数値データ型を必要とします。</span><span class="sxs-lookup"><span data-stu-id="0fc80-142">The key sequence column is a special kind of nested key that is used only in sequence clustering models, and requires a unique numeric data type.</span></span> <span data-ttu-id="0fc80-143">たとえば、整数と日付はどちらも key sequence 列として使用できますが、すべてのシーケンス値が一意である必要があります。</span><span class="sxs-lookup"><span data-stu-id="0fc80-143">For example, integers and dates can both be used as a key sequence column, but all sequence values must be unique.</span></span> <span data-ttu-id="0fc80-144">シーケンス クラスター モデルには、key sequence 列のほかに、モデル化される属性 (購入された製品など) を表す入れ子になったテーブル キーもあります。</span><span class="sxs-lookup"><span data-stu-id="0fc80-144">In addition to the key sequence column, a sequence clustering model also has a nested table key that represents the attribute that is being modeled, such as the products that have been purchased.</span></span>  
  
### <a name="using-non-key-nested-columns-from-a-nested-table"></a><span data-ttu-id="0fc80-145">入れ子になったテーブルのキー以外の入れ子になった列の使用</span><span class="sxs-lookup"><span data-stu-id="0fc80-145">Using Non-Key Nested Columns from a Nested Table</span></span>  
 <span data-ttu-id="0fc80-146">ケース テーブルと入れ子になったテーブルの間の結合を定義し、入れ子になったテーブルのキーとして使用する興味深い一意の属性を含む列を選択したら、入れ子になったテーブルのその他の列を追加して、モデルへの入力として使用することができます。</span><span class="sxs-lookup"><span data-stu-id="0fc80-146">After you have defined the join between the case table and the nested table, and you have chosen a column that contains interesting and unique attributes to use as the nested table key, you can include other columns from the nested table to use as input to the model.</span></span> <span data-ttu-id="0fc80-147">入れ子になったテーブルのすべての列を、入力、予測と入力、または予測のみに使用できます。</span><span class="sxs-lookup"><span data-stu-id="0fc80-147">All columns from the nested table can be used for input, prediction and input, or for prediction only.</span></span>  
  
 <span data-ttu-id="0fc80-148">たとえば入れ子になったテーブルに、**Product**、**ProductQuantity\*\*\*\*ProductPrice** の各列が含まれていて、入れ子になったテーブルのキーとして **Product** を選択した場合に、**ProductQuantity** をマイニング構造に追加して入力として使用することができます。</span><span class="sxs-lookup"><span data-stu-id="0fc80-148">For example, if the nested table contains the columns **Product**, **ProductQuantity**, and **ProductPrice**, you might choose **Product** as the nested table key, but add **ProductQuantity** to the mining structure to use as input.</span></span>  
  
## <a name="filtering-nested-table-data"></a><span data-ttu-id="0fc80-149">入れ子になったテーブルのデータのフィルター処理</span><span class="sxs-lookup"><span data-stu-id="0fc80-149">Filtering Nested Table Data</span></span>  
 <span data-ttu-id="0fc80-150">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]では、データ マイニング モデルのトレーニング用やテスト用のデータに対するフィルターを作成できます。</span><span class="sxs-lookup"><span data-stu-id="0fc80-150">In [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], you can create filters on the data that is used to train or test a data mining model.</span></span> <span data-ttu-id="0fc80-151">フィルターを使用すると、モデルの構成に影響を与えたり、ケースのサブセットでモデルをテストしたりできます。</span><span class="sxs-lookup"><span data-stu-id="0fc80-151">A filer can be used to affect the composition of the model, or to test the model on a subset of cases.</span></span> <span data-ttu-id="0fc80-152">入れ子になったテーブルにフィルターを適用することもできます。</span><span class="sxs-lookup"><span data-stu-id="0fc80-152">Filters can also be applied to nested tables.</span></span> <span data-ttu-id="0fc80-153">ただし、入れ子になったテーブルで使用できる構文には制限があります。</span><span class="sxs-lookup"><span data-stu-id="0fc80-153">However, there are limitations on the syntax that can be used with nested tables.</span></span>  
  
 <span data-ttu-id="0fc80-154">入れ子になったテーブルでは、属性の存在の有無をテストするためによくフィルターが使用されます。</span><span class="sxs-lookup"><span data-stu-id="0fc80-154">Often when you apply a filter to a nested table you are testing for the existence or nonexistence of an attribute.</span></span> <span data-ttu-id="0fc80-155">たとえば、フィルターを適用することにより、モデルで使用するケースを、入れ子になったテーブルに指定した値を持つケースのみに制限したり、</span><span class="sxs-lookup"><span data-stu-id="0fc80-155">For example, you can apply a filter that restricts the cases used in the model to only those cases that have a specified value in the nested table.</span></span> <span data-ttu-id="0fc80-156">特定の品目を購入したことがない顧客のみに制限したりすることができます。</span><span class="sxs-lookup"><span data-stu-id="0fc80-156">Or, you could restrict the cases used in the model to customers who have not purchased a particular item.</span></span>  
  
 <span data-ttu-id="0fc80-157">入れ子になったテーブルのフィルターを作成するときには、"より大きい" や "より小さい" などの演算子を使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="0fc80-157">When you create filters on a nested table, you can also use operators such as greater than or less than.</span></span> <span data-ttu-id="0fc80-158">たとえば、モデルで使用するケースを、対象の製品を n 単位以上購入した顧客だけに制限することができます。</span><span class="sxs-lookup"><span data-stu-id="0fc80-158">For example, you could restrict the cases used in the model to customers who had purchased at least n units of the target product.</span></span> <span data-ttu-id="0fc80-159">入れ子になったテーブルの属性にフィルターを適用できることによってモデルのカスタマイズの幅が大きく広がります。</span><span class="sxs-lookup"><span data-stu-id="0fc80-159">The ability to filter on nested table attributes provides great flexibility for customizing models.</span></span>  
  
 <span data-ttu-id="0fc80-160">モデル フィルターの作成と使用の方法の詳細については、「[マイニング モデルのフィルター選択 &#40;Analysis Services - データ マイニング&#41;](mining-models-analysis-services-data-mining.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0fc80-160">For more information about how to create and use model filters, see [Filters for Mining Models &#40;Analysis Services - Data Mining&#41;](mining-models-analysis-services-data-mining.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0fc80-161">参照</span><span class="sxs-lookup"><span data-stu-id="0fc80-161">See Also</span></span>  
 <span data-ttu-id="0fc80-162">[データマイニングアルゴリズム &#40;Analysis Services-データマイニング&#41;](data-mining-algorithms-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="0fc80-162">[Data Mining Algorithms &#40;Analysis Services - Data Mining&#41;](data-mining-algorithms-analysis-services-data-mining.md) </span></span>  
 [<span data-ttu-id="0fc80-163">マイニング構造 (Analysis Services - データ マイニング)</span><span class="sxs-lookup"><span data-stu-id="0fc80-163">Mining Structures &#40;Analysis Services - Data Mining&#41;</span></span>](mining-structures-analysis-services-data-mining.md)  
  
  