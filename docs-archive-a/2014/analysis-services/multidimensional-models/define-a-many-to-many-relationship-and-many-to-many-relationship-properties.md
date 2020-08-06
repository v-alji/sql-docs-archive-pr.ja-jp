---
title: 多対多リレーションシップと多対多リレーションシップのプロパティを定義します。Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- many-to-many relationships [Analysis Services]
ms.assetid: edb5f61a-a581-467a-a367-134b7f9b849f
author: minewiskan
ms.author: owend
ms.openlocfilehash: 1cd5d46ce07ff8eb6a3893c0dac261797c6ef19e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644663"
---
# <a name="define-a-many-to-many-relationship-and-many-to-many-relationship-properties"></a><span data-ttu-id="22be9-102">多対多のリレーションシップと多対多のリレーションシップのプロパティの定義</span><span class="sxs-lookup"><span data-stu-id="22be9-102">Define a Many-to-Many Relationship and Many-to-Many Relationship Properties</span></span>
  <span data-ttu-id="22be9-103">このトピックでは、多対多ディメンションを使用する状況と作成方法を含め、Analysis Services 内の多対多ディメンションについて説明します。</span><span class="sxs-lookup"><span data-stu-id="22be9-103">This topic explains many-to-many dimensions in Analysis Services, including when to use them and how to create them.</span></span>  
  
## <a name="introduction"></a><span data-ttu-id="22be9-104">はじめに</span><span class="sxs-lookup"><span data-stu-id="22be9-104">Introduction</span></span>  
 <span data-ttu-id="22be9-105">Analysis Services は、多対多ディメンションをサポートし、従来のスター スキーマで記述できる以上に複雑な分析に対応できます。</span><span class="sxs-lookup"><span data-stu-id="22be9-105">Analysis Services supports many-to-many dimensions, allowing for more complex analytics than what can be described in a classic star schema.</span></span> <span data-ttu-id="22be9-106">従来のスター スキーマでは、すべてのディメンションがファクト テーブル内で一対多のリレーションシップを持ちます。</span><span class="sxs-lookup"><span data-stu-id="22be9-106">In a classic star schema, all dimensions have a one-to-many relationship with a fact table.</span></span> <span data-ttu-id="22be9-107">各ファクトは 1 つのディメンション メンバーと結合しています。1 つのディメンション メンバーは複数のファクトに関連付けられます。</span><span class="sxs-lookup"><span data-stu-id="22be9-107">Each fact joins to one dimension member; a single dimension member is associated with many facts.</span></span>  
  
 <span data-ttu-id="22be9-108">多対多では、単一のファクト (口座残高など) を、同じディメンションの複数のメンバーに関連付けできるようにすること (共同名義口座の残高を、その口座の複数の所有者に帰属させることができる) で、モデル化に関するこの制約を取り除きます。</span><span class="sxs-lookup"><span data-stu-id="22be9-108">Many-to-many removes this modeling restriction by enabling a fact (such as an account balance) to be associated with multiple members of the same dimension (the balance of a joint account can be attributed to two or more owners of a joint account).</span></span>  
  
 <span data-ttu-id="22be9-109">概念的には、Analysis Services 内の多対多ディメンションのリレーションシップは、従来のモデル内の多対多リレーションシップと同等であり、同じ種類のシナリオに対応しています。</span><span class="sxs-lookup"><span data-stu-id="22be9-109">Conceptually, a many-to-many dimensional relationship in Analysis Services is equivalent to many-to-many relationships in a relational model, supporting the same kinds of scenarios.</span></span> <span data-ttu-id="22be9-110">多対多の一般的な例として、次のものを挙げることができます。</span><span class="sxs-lookup"><span data-stu-id="22be9-110">Common examples of many-to-many include:</span></span>  
  
-   <span data-ttu-id="22be9-111">学生は複数のコースに登録され、各コースに複数の学生が参加します。</span><span class="sxs-lookup"><span data-stu-id="22be9-111">Students are enrolled in many courses; each course has many students.</span></span>  
  
-   <span data-ttu-id="22be9-112">医師は複数の患者を担当し、患者は複数の医師から対応を受けます。</span><span class="sxs-lookup"><span data-stu-id="22be9-112">Doctors have many patients; patients have many doctors.</span></span>  
  
-   <span data-ttu-id="22be9-113">顧客は複数の銀行口座を持ち、銀行口座は複数の顧客に帰属する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="22be9-113">Customers have many bank accounts; bank accounts might belong to more than one customer.</span></span>  
  
-   <span data-ttu-id="22be9-114">Adventure Works では、多くの顧客が複数の購入動機で 1 回の製品注文をし、1 つの購入動機が複数の注文に結び付くことがあります。</span><span class="sxs-lookup"><span data-stu-id="22be9-114">In Adventure Works, many customers have many reasons for ordering a product, and a sales reason can be associated with many orders.</span></span>  
  
 <span data-ttu-id="22be9-115">分析の観点では、多対多の関係で解決する問題は、ディメンションのリレーションシップを基準としたカウントまたは合計に関する正確な表現形式 (通常は特定のディメンション メンバーに関する計算を実行するときに、二重カウントを除去します) です。</span><span class="sxs-lookup"><span data-stu-id="22be9-115">Analytically, the problem that a many-to-many relationship solves is accurate representation of a count or sum relative to the dimensional relationship (usually by eliminating double-counts when performing calculations for a specific dimension member).</span></span> <span data-ttu-id="22be9-116">この点を明確にするのには例が必要です。</span><span class="sxs-lookup"><span data-stu-id="22be9-116">An example is necessary to clarify this point.</span></span> <span data-ttu-id="22be9-117">複数のカテゴリに属する 1 つの製品またはサービスについて考えます。</span><span class="sxs-lookup"><span data-stu-id="22be9-117">Consider a product or service that belongs to more than one category.</span></span> <span data-ttu-id="22be9-118">仮にカテゴリごとにサービスをカウントする場合は、両方のカテゴリに属する 1 つのサービスを、どちらにカテゴリにも含めたいと考えます。</span><span class="sxs-lookup"><span data-stu-id="22be9-118">If you were counting the number of services by category, you would want a service belonging to both categories to be included in each one.</span></span> <span data-ttu-id="22be9-119">同時に、提供しているサービスの数を過大に表示することも避けたいと考えます。</span><span class="sxs-lookup"><span data-stu-id="22be9-119">At the same time, you would not want to overstate the number of services that you provide.</span></span> <span data-ttu-id="22be9-120">多対多ディメンションのリレーションシップを指定することで、カテゴリごとまたはサービスごとのクエリを実行するときに、正確な結果を取得できる可能性がいっそう高くなります。</span><span class="sxs-lookup"><span data-stu-id="22be9-120">By specifying the many-to-many dimensional relationship, you are more likely to get the correct results back when querying by category or by service.</span></span> <span data-ttu-id="22be9-121">ただし、この考え方が適切であることを確認するために、全体的なテストが常に必要です。</span><span class="sxs-lookup"><span data-stu-id="22be9-121">However, thorough testing is always necessary to ensure that this is the case.</span></span>  
  
 <span data-ttu-id="22be9-122">構造的には、多対多ディメンションのリレーションシップを作成することは、リレーショナル データ モデル内で多対多を作成する方法に似ています。</span><span class="sxs-lookup"><span data-stu-id="22be9-122">Structurally, creating a many-to-many dimensional relationship is similar to how you might create many-to-many in a relational data model.</span></span> <span data-ttu-id="22be9-123">リレーショナル モデルは *交差テーブル* を使用して行のアソシエーションを格納するのに対し、多次元モデルは *中間メジャー グループ*を使用します。</span><span class="sxs-lookup"><span data-stu-id="22be9-123">Whereas a relational model uses a *junction table* to store row associations, a multidimensional model uses an *intermediate measure group*.</span></span> <span data-ttu-id="22be9-124">中間メジャー グループとは、異なるディメンションから取得したメンバーをマップするテーブルを参照するために使用する用語です。</span><span class="sxs-lookup"><span data-stu-id="22be9-124">Intermediate measure group is the term we use to refer to a table that maps members from different dimensions.</span></span>  
  
 <span data-ttu-id="22be9-125">視覚的には、多対多ディメンションのリレーションシップはキューブ図では表示されません。</span><span class="sxs-lookup"><span data-stu-id="22be9-125">Visually, a many-to-many dimensional relationship is not indicated in a cube diagram.</span></span> <span data-ttu-id="22be9-126">代わりに、[ディメンションの使用法] タブを使用して、モデル内にあるすべての多対多リレーションシップをすばやく識別することができます。</span><span class="sxs-lookup"><span data-stu-id="22be9-126">Instead, use the Dimension Usage tab to quickly identify any many-to-many relationships in a model.</span></span> <span data-ttu-id="22be9-127">多対多リレーションシップは、次のアイコンによって示されます。</span><span class="sxs-lookup"><span data-stu-id="22be9-127">A many-to-many relationship is indicated by the following icon.</span></span>  
  
 <span data-ttu-id="22be9-128">![ディメンション使用法内の多対多アイコン](../media/ssas-m2m-icondimusage.png "ディメンション使用法内の多対多アイコン")</span><span class="sxs-lookup"><span data-stu-id="22be9-128">![Many-to-many icon in dimension usage](../media/ssas-m2m-icondimusage.png "Many-to-many icon in dimension usage")</span></span>  
  
 <span data-ttu-id="22be9-129">ボタンをクリックすると、[リレーションシップの定義] ダイアログ ボックスが開き、リレーションシップの種類が多対多であることを確認し、リレーションシップ内で使用されている中間メジャー グループを表示することができます。</span><span class="sxs-lookup"><span data-stu-id="22be9-129">Click the button to open the Define Relationship dialog box to verify the relationship type is many-to-many, and to view which intermediate measure group is used in the relationship.</span></span>  
  
 <span data-ttu-id="22be9-130">![ディメンションの使用法の [リレーションシップの定義] ボタン](../media/ssas-m2m-btndimusage.png "ディメンションの使用法の [リレーションシップの定義] ボタン")</span><span class="sxs-lookup"><span data-stu-id="22be9-130">![Define Relationship button  in dimension usage](../media/ssas-m2m-btndimusage.png "Define Relationship button  in dimension usage")</span></span>  
  
 <span data-ttu-id="22be9-131">これ以降のセクションでは、多対多リレーションシップを設定する方法と、モデルの動作をテストする方法を学習します。</span><span class="sxs-lookup"><span data-stu-id="22be9-131">In subsequent sections, you will learn how to set up a many-to-many dimension and test model behaviors.</span></span> <span data-ttu-id="22be9-132">代わりに、追加情報を確認する場合や、チュートリアルを最初に試す場合は、この記事の最後にある「 **詳細情報** 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="22be9-132">If you would rather review additional information or try tutorials first, see **Learn More** at the end of this article.</span></span>  
  
## <a name="create-a-many-to-many-dimension"></a><span data-ttu-id="22be9-133">多対多ディメンションの作成</span><span class="sxs-lookup"><span data-stu-id="22be9-133">Create a many-to-many dimension</span></span>  
 <span data-ttu-id="22be9-134">単純な多対多リレーションシップには、多対多のカーディナリティを含む 2 つのディメンション、メンバー アソシエーションを格納するための中間メジャー グループ、総売上や銀行口座の残高の合計など測定可能なデータを含むファクト メジャー グループが含まれています。</span><span class="sxs-lookup"><span data-stu-id="22be9-134">A simple many-to-many relationship includes two dimensions having a many-to-many cardinality, an intermediate measure group for storing member associations, and a fact measure group containing measurable data, such as sum of total sales or the balance of a bank account.</span></span>  
  
 <span data-ttu-id="22be9-135">多対多リレーションシップ内の各ディメンションには、DSV 内の対応テーブルが含まれている可能性があり、その場合は、モデル内の各ディメンションが、データ ソース内の既存のテーブルに基づいています。</span><span class="sxs-lookup"><span data-stu-id="22be9-135">Dimensions in a many-to-many relationship might have correspondent tables in the DSV, where each dimension in the model is based on an existing table in a data source.</span></span> <span data-ttu-id="22be9-136">逆に、モデル内のディメンションが、DSV 内の少数の物理テーブルや複数の物理テーブルから派生した可能性もあります。</span><span class="sxs-lookup"><span data-stu-id="22be9-136">Conversely, the dimensions in your model might derive from fewer or different physical tables in the DSV.</span></span> <span data-ttu-id="22be9-137">Sales Reasons と Sales Orders を適切な例として使用して、Adventure Works のサンプル キューブはモデルのみのデータ構造として存在するディメンションを活用して多対多の関係を示しますが、DSV 内に物理的な同等の存在はありません。</span><span class="sxs-lookup"><span data-stu-id="22be9-137">Using Sales Reasons and Sales Orders as a case in point, the Adventure Works sample cube demonstrates a many-to-many relationship using dimensions that exist as model-only data structures, without physical counterparts in the DSV.</span></span> <span data-ttu-id="22be9-138">Sales Order ディメンションは、基になるデータ ソース内のディメンション テーブルではなく、ファクト テーブルに基づいています。</span><span class="sxs-lookup"><span data-stu-id="22be9-138">The Sales Order dimension is based on a fact table, rather than a dimension table, in the underlying data source.</span></span>  
  
 <span data-ttu-id="22be9-139">次の手順では、多対多リレーションシップにどのエンティティが参加しているかを既に把握していることを想定しています。</span><span class="sxs-lookup"><span data-stu-id="22be9-139">The next procedure assumes that you already know which entities participate in the many-to-many relationship.</span></span> <span data-ttu-id="22be9-140">詳細情報を確認するには、「 **詳細情報** 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="22be9-140">See **Learn More** for further study.</span></span>  
  
 <span data-ttu-id="22be9-141">多対多リレーションシップを作成する手順を示すために、Adventure Works のサンプル キューブ内にある多対多リレーションシップの 1 つを、この手順で作成し直します。</span><span class="sxs-lookup"><span data-stu-id="22be9-141">To illustrate the steps used to create a many-to-many relationship, this procedure re-creates one of the many-to-many relationships in the Adventure Works sample cube.</span></span> <span data-ttu-id="22be9-142">リレーショナル データベース エンジンのインスタンスにソース データ (つまり、Adventure Works サンプル データ ウェアハウス) を既にインストールしてある場合は、次の手順に従うことができます。</span><span class="sxs-lookup"><span data-stu-id="22be9-142">If you have the source data (that is, the Adventure Works sample data warehouse) installed on a relational database engine instance, you can follow these steps.</span></span>  
  
#### <a name="step-1-verify-dsv-relationships"></a><span data-ttu-id="22be9-143">手順 1: DSV リレーションシップの確認</span><span class="sxs-lookup"><span data-stu-id="22be9-143">Step 1: Verify DSV relationships</span></span>  
  
1.  <span data-ttu-id="22be9-144">SQL Server データ ツールの多次元プロジェクトで、SQL Server データベース エンジンのインスタンスでホストされている Adventure Works DW 2012 リレーショナル データ ウェアハウスに接続するデータ ソースを作成します。</span><span class="sxs-lookup"><span data-stu-id="22be9-144">In SQL Server Data Tools, in a multidimensional project, create a data source to the Adventure Works DW 2012 relational data warehouse, hosted on a SQL Server Database Engine instance.</span></span>  
  
2.  <span data-ttu-id="22be9-145">次の既存のテーブルを使用して、データ ソース ビューを作成します。</span><span class="sxs-lookup"><span data-stu-id="22be9-145">Create a Data Source View using the following existing tables:</span></span>  
  
    -   <span data-ttu-id="22be9-146">FactInternetSales</span><span class="sxs-lookup"><span data-stu-id="22be9-146">FactInternetSales</span></span>  
  
    -   <span data-ttu-id="22be9-147">FactInternetSalesReason</span><span class="sxs-lookup"><span data-stu-id="22be9-147">FactInternetSalesReason</span></span>  
  
    -   <span data-ttu-id="22be9-148">DimSalesReason</span><span class="sxs-lookup"><span data-stu-id="22be9-148">DimSalesReason</span></span>  
  
3.  <span data-ttu-id="22be9-149">多対多リレーションシップで使用することを計画しているすべてのテーブルが、DSV 内で主キーのリレーションシップを通じて関連付けられていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="22be9-149">Verify that all of the tables you plan to use in the many-to-many relationships are related in the DSV through primary key relationships.</span></span> <span data-ttu-id="22be9-150">これは、これ以降の手順で中間メジャー グループへのリンクを確立するための要件です。</span><span class="sxs-lookup"><span data-stu-id="22be9-150">This is a requirement for establishing a link to the intermediate measure group in a subsequent step.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="22be9-151">基になるデータ ソースが主キー リレーションシップや外部キー リレーションシップを提供していない場合は、DSV 内でそれらのリレーションシップを手動で作成できます。</span><span class="sxs-lookup"><span data-stu-id="22be9-151">If the underlying data source does not provide primary and foreign key relationships, you can create the relationships manually in the DSV.</span></span> <span data-ttu-id="22be9-152">詳細については、「[データ ソース ビューでの論理リレーションシップの定義 &#40;Analysis Services&#41;](define-logical-relationships-in-a-data-source-view-analysis-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="22be9-152">For more information, see [Define Logical Relationships in a Data Source View &#40;Analysis Services&#41;](define-logical-relationships-in-a-data-source-view-analysis-services.md).</span></span>  
  
     <span data-ttu-id="22be9-153">この手順で使用するテーブルが主キーを使用してリンクされていることを、次の例で確認します。</span><span class="sxs-lookup"><span data-stu-id="22be9-153">The following example confirms that the tables used in this procedure are linked using primary keys.</span></span>  
  
     <span data-ttu-id="22be9-154">![関連テーブルを示す DSV](../media/ssas-m2m-dsvpkeys.PNG "関連テーブルを示す DSV")</span><span class="sxs-lookup"><span data-stu-id="22be9-154">![DSV showing related tables](../media/ssas-m2m-dsvpkeys.PNG "DSV showing related tables")</span></span>  
  
#### <a name="step-2-create-dimensions-and-measure-groups"></a><span data-ttu-id="22be9-155">手順 2: ディメンションとメジャー グループの作成</span><span class="sxs-lookup"><span data-stu-id="22be9-155">Step 2: Create dimensions and measure groups</span></span>  
  
1.  <span data-ttu-id="22be9-156">SQL Server データ ツールの多次元プロジェクトで、 **[ディメンション]** を右クリックし、 **[新しいディメンション]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="22be9-156">In SQL Server Data Tools, in a multidimensional project, right-click **Dimensions** and select **New Dimension**.</span></span>  
  
2.  <span data-ttu-id="22be9-157">既存のテーブル **DimSalesReason**に基づいて新しいディメンションを作成します。</span><span class="sxs-lookup"><span data-stu-id="22be9-157">Create a new dimension based on existing table, **DimSalesReason**.</span></span> <span data-ttu-id="22be9-158">ソースを指定するときに、すべての既定値をそのまま使用します。</span><span class="sxs-lookup"><span data-stu-id="22be9-158">Accept all of the default values when specifying the source.</span></span>  
  
     <span data-ttu-id="22be9-159">属性に関しては、すべてを選択します。</span><span class="sxs-lookup"><span data-stu-id="22be9-159">For attributes, select all.</span></span>  
  
     <span data-ttu-id="22be9-160">![新しいディメンション内の属性リスト](../media/ssas-m2m-dimsalesreason.PNG "新しいディメンション内の属性リスト")</span><span class="sxs-lookup"><span data-stu-id="22be9-160">![Attributes list in new dimension](../media/ssas-m2m-dimsalesreason.PNG "Attributes list in new dimension")</span></span>  
  
3.  <span data-ttu-id="22be9-161">既存のテーブル Fact Internet Sales に基づいて 2 番目のディメンションを作成します。</span><span class="sxs-lookup"><span data-stu-id="22be9-161">Create a second dimension based on existing table, Fact Internet Sales.</span></span> <span data-ttu-id="22be9-162">これはファクト テーブルですが、Sales Order 情報を格納しています。</span><span class="sxs-lookup"><span data-stu-id="22be9-162">Although this is a fact table, it contains Sales Order information.</span></span> <span data-ttu-id="22be9-163">このテーブルを使用して、Sales Order ディメンションを作成します。</span><span class="sxs-lookup"><span data-stu-id="22be9-163">We'll use it to build a Sales Order dimension.</span></span>  
  
4.  <span data-ttu-id="22be9-164">[基になる情報の指定] で、[名前] 列を指定する必要があることを示す警告が表示されます。</span><span class="sxs-lookup"><span data-stu-id="22be9-164">In Specify Source Information, you will see a warning that indicates a Name column must be specified.</span></span> <span data-ttu-id="22be9-165">[名前] として、 **SalesOrderNumber** を選択します。</span><span class="sxs-lookup"><span data-stu-id="22be9-165">Choose **SalesOrderNumber** as the Name.</span></span>  
  
     <span data-ttu-id="22be9-166">![名前列を示す Sales Order ディメンション](../media/ssas-m2m-dimsalesordersource.PNG "名前列を示す Sales Order ディメンション")</span><span class="sxs-lookup"><span data-stu-id="22be9-166">![Sales Order dimension showing the name column](../media/ssas-m2m-dimsalesordersource.PNG "Sales Order dimension showing the name column")</span></span>  
  
5.  <span data-ttu-id="22be9-167">ウィザードの次のページで、属性を選択します。</span><span class="sxs-lookup"><span data-stu-id="22be9-167">On the next page of the wizard, choose the attributes.</span></span> <span data-ttu-id="22be9-168">この例では、 **SalesOrderNumber**のみを選択できます。</span><span class="sxs-lookup"><span data-stu-id="22be9-168">In this example, you can select just **SalesOrderNumber**.</span></span>  
  
     <span data-ttu-id="22be9-169">![属性リストを示す Sales order ディメンション](../media/ssas-m2m-dimsalesorderattrib.PNG "属性リストを示す Sales order ディメンション")</span><span class="sxs-lookup"><span data-stu-id="22be9-169">![Sales order dimension showing attribute list](../media/ssas-m2m-dimsalesorderattrib.PNG "Sales order dimension showing attribute list")</span></span>  
  
6.  <span data-ttu-id="22be9-170">そのディメンションを **Dim Sales Orders**という名前に変更します。その結果、ディメンションに関して、一貫性のある名前付け規約を使用できます。</span><span class="sxs-lookup"><span data-stu-id="22be9-170">Rename the dimension to **Dim Sales Orders**, so that you have a consistent naming convention for the dimensions.</span></span>  
  
     <span data-ttu-id="22be9-171">![ディメンションの名前変更を示すウィザード ページ](../media/ssas-m2m-dimsalesorders.PNG "ディメンションの名前変更を示すウィザード ページ")</span><span class="sxs-lookup"><span data-stu-id="22be9-171">![Wizard page showing dimension rename](../media/ssas-m2m-dimsalesorders.PNG "Wizard page showing dimension rename")</span></span>  
  
7.  <span data-ttu-id="22be9-172">**[キューブ]** を右クリックし、 **[新しいキューブ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="22be9-172">Right-click **Cubes** and select **New Cube**.</span></span>  
  
8.  <span data-ttu-id="22be9-173">メジャー グループ テーブルで、 **FactInternetSales** と **FactInternetSalesReason**を選択します。</span><span class="sxs-lookup"><span data-stu-id="22be9-173">In measure group tables, choose **FactInternetSales** and **FactInternetSalesReason**.</span></span>  
  
     <span data-ttu-id="22be9-174">**FactInternetSales** を選択する理由は、キューブで使用するメジャーがこの中に含まれていることです。</span><span class="sxs-lookup"><span data-stu-id="22be9-174">You are choosing **FactInternetSales** because it contains the measures you want to use in the cube.</span></span> <span data-ttu-id="22be9-175">**FactInternetSalesReason** を選択する理由は、これが、販売注文を購入動機に関連付けるメンバー アソシエーション データを提供する中間メジャー グループであることです。</span><span class="sxs-lookup"><span data-stu-id="22be9-175">You are choosing **FactInternetSalesReason** because it is the intermediate measure group, providing member association data that relates sales orders to sales reasons.</span></span>  
  
9. <span data-ttu-id="22be9-176">各ファクト テーブルに対応するメジャーを選択します。</span><span class="sxs-lookup"><span data-stu-id="22be9-176">Choose measures for each fact table.</span></span>  
  
     <span data-ttu-id="22be9-177">モデルを簡略化するために、すべてのメジャーをクリアしてから、リストの下部にある **Sales Amount** と **Fact Internet Sales Count** のみを選択します。</span><span class="sxs-lookup"><span data-stu-id="22be9-177">To simplify your model, clear all the measures, and then select just **Sales Amount** and **Fact Internet Sales Count** at the bottom of the list.</span></span> <span data-ttu-id="22be9-178">**FactInternetSalesReason** にはただ 1 つのメジャーがあることから、このメジャーが自動的に選択されます。</span><span class="sxs-lookup"><span data-stu-id="22be9-178">The **FactInternetSalesReason** only has one measure, so it is selected for you automatically.</span></span>  
  
10. <span data-ttu-id="22be9-179">ディメンション リストで、 **Dim Sales Reason** と **Dim Sales Orders**が表示されます。</span><span class="sxs-lookup"><span data-stu-id="22be9-179">In the dimension list, you should see **Dim Sales Reason** and **Dim Sales Orders**.</span></span>  
  
     <span data-ttu-id="22be9-180">[新しいディメンションの選択] ページで、 **Fact Internet Sales Dimension**に対応する新しいディメンションを作成するように要求されます。</span><span class="sxs-lookup"><span data-stu-id="22be9-180">In the Select New Dimensions page, the wizard prompts you to create a new dimension for **Fact Internet Sales Dimension**.</span></span> <span data-ttu-id="22be9-181">このディメンションは必要ないため、リストからこのディメンションをクリアできます。</span><span class="sxs-lookup"><span data-stu-id="22be9-181">You do not need this dimension, so you can clear it from the list.</span></span>  
  
11. <span data-ttu-id="22be9-182">キューブに名前を付け、 **[完了]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="22be9-182">Name the cube and click **Finish**.</span></span>  
  
#### <a name="step-3-define-many-to-many-relationship"></a><span data-ttu-id="22be9-183">手順 3: 多対多リレーションシップの定義</span><span class="sxs-lookup"><span data-stu-id="22be9-183">Step 3: Define Many-to-Many relationship</span></span>  
  
1.  <span data-ttu-id="22be9-184">キューブデザイナーで、[ディメンションの使用法] タブをクリックします。 **Dim Sales Reason**と**Fact Internet Sales**の間には、既に多対多のリレーションシップがあることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="22be9-184">In cube designer, click Dimension Usage tab. Notice that there is already a many-to-many relationship between **Dim Sales Reason** and **Fact Internet Sales**.</span></span> <span data-ttu-id="22be9-185">次のアイコンが、多対多リレーションシップを示していることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="22be9-185">Recall that the following icon indicates a many-to-many relationship.</span></span>  
  
     <span data-ttu-id="22be9-186">![ディメンション使用法内の多対多アイコン](../media/ssas-m2m-icondimusage.png "ディメンション使用法内の多対多アイコン")</span><span class="sxs-lookup"><span data-stu-id="22be9-186">![Many-to-many icon in dimension usage](../media/ssas-m2m-icondimusage.png "Many-to-many icon in dimension usage")</span></span>  
  
2.  <span data-ttu-id="22be9-187">**Dim Sales Reason** と **Fact Internet Sales**の交差セルをクリックし、ボタンをクリックして [リレーションシップの定義] ダイアログ ボックスを開きます。</span><span class="sxs-lookup"><span data-stu-id="22be9-187">Click on the intersection cell between **Dim Sales Reason** and **Fact Internet Sales**, and then click the button to open the Define Relationship dialog box.</span></span>  
  
     <span data-ttu-id="22be9-188">このダイアログ ボックスを使用して、多対多リレーションシップを指定できることがわかります。</span><span class="sxs-lookup"><span data-stu-id="22be9-188">You can see that this dialog box is used to specify a many-to-many relationship.</span></span> <span data-ttu-id="22be9-189">代わりに、標準のリレーションシップを持つディメンションを追加する場合は、このダイアログ ボックスを使用して多対多に変更することになります。</span><span class="sxs-lookup"><span data-stu-id="22be9-189">If you were adding dimensions that had a regular relationship instead, you would use this dialog box to change it to many-to-many.</span></span>  
  
     <span data-ttu-id="22be9-190">![ディメンションの使用法の [リレーションシップの定義] ボタン](../media/ssas-m2m-btndimusage.png "ディメンションの使用法の [リレーションシップの定義] ボタン")</span><span class="sxs-lookup"><span data-stu-id="22be9-190">![Define Relationship button  in dimension usage](../media/ssas-m2m-btndimusage.png "Define Relationship button  in dimension usage")</span></span>  
  
3.  <span data-ttu-id="22be9-191">プロジェクトを、Analysis Services 多次元インスタンスに配置します。</span><span class="sxs-lookup"><span data-stu-id="22be9-191">Deploy the project to an Analysis Services multidimensional instance.</span></span> <span data-ttu-id="22be9-192">次の手順で、Excel でこのキューブを参照し、その動作を確認します。</span><span class="sxs-lookup"><span data-stu-id="22be9-192">In the next step, you will browse the cube in Excel to verify its behaviors.</span></span>  
  
## <a name="testing-many-to-many"></a><span data-ttu-id="22be9-193">多対多のテスト</span><span class="sxs-lookup"><span data-stu-id="22be9-193">Testing Many-to-Many</span></span>  
 <span data-ttu-id="22be9-194">キューブ内で多対多リレーションシップを定義する場合は、クエリが正しい結果を返すことを確認するために、テストが必要不可欠です。</span><span class="sxs-lookup"><span data-stu-id="22be9-194">When you define a many-to-many relationship in a cube, testing is imperative to ensure queries return expected results.</span></span> <span data-ttu-id="22be9-195">エンド ユーザーが使用する予定のクライアント アプリケーション ツールで、キューブをテストする必要があります。</span><span class="sxs-lookup"><span data-stu-id="22be9-195">You should test the cube using the client application tool that will be used by end-users.</span></span> <span data-ttu-id="22be9-196">次の手順で、Excel を使用してキューブに接続し、クエリ結果を確認します。</span><span class="sxs-lookup"><span data-stu-id="22be9-196">In this next procedure, you will use Excel to connect to the cube and verify query results.</span></span>  
  
#### <a name="browse-the-cube-in-excel"></a><span data-ttu-id="22be9-197">Excel 内でのキューブの参照</span><span class="sxs-lookup"><span data-stu-id="22be9-197">Browse the cube in Excel</span></span>  
  
1.  <span data-ttu-id="22be9-198">プロジェクトを配置し、キューブを参照して、集計が有効であることを確認します。</span><span class="sxs-lookup"><span data-stu-id="22be9-198">Deploy the project and then browse the cube to confirm the aggregations are valid.</span></span>  
  
2.  <span data-ttu-id="22be9-199">Excel で、Analysis Services の [ **Data**  |  **その他のソース**のデータ] をクリックし  |  **From Analysis Services**ます。</span><span class="sxs-lookup"><span data-stu-id="22be9-199">In Excel, click **Data** | **From Other Sources** | **From Analysis Services**.</span></span> <span data-ttu-id="22be9-200">サーバーの名前を入力し、データベースとキューブを選択します。</span><span class="sxs-lookup"><span data-stu-id="22be9-200">Enter the name of the server, choose the database and cube.</span></span>  
  
3.  <span data-ttu-id="22be9-201">次のものを使用するピボットテーブルを作成します。</span><span class="sxs-lookup"><span data-stu-id="22be9-201">Create a PivotTable that uses the following:</span></span>  
  
    -   <span data-ttu-id="22be9-202">値として**Sales Amount**</span><span class="sxs-lookup"><span data-stu-id="22be9-202">**Sales Amount** as the Value</span></span>  
  
    -   <span data-ttu-id="22be9-203">列で**Sales Reason Name**</span><span class="sxs-lookup"><span data-stu-id="22be9-203">**Sales Reason Name** on Columns</span></span>  
  
    -   <span data-ttu-id="22be9-204">行で**Sales Order Number**</span><span class="sxs-lookup"><span data-stu-id="22be9-204">**Sales Order Number** on Rows</span></span>  
  
4.  <span data-ttu-id="22be9-205">結果を分析します。</span><span class="sxs-lookup"><span data-stu-id="22be9-205">Analyze the results.</span></span> <span data-ttu-id="22be9-206">サンプル データを使用しているため、最初は、すべての販売注文が同じ値になっているという印象を受けます。</span><span class="sxs-lookup"><span data-stu-id="22be9-206">Because we are using sample data, the initial impression is that all sales orders have identical values.</span></span> <span data-ttu-id="22be9-207">ただし、下へスクロールすると、データに差異があることに気が付きます。</span><span class="sxs-lookup"><span data-stu-id="22be9-207">However, if you scroll down, you begin to see data variation.</span></span>  
  
     <span data-ttu-id="22be9-208">途中まで進んだところで、注文番号 **SO5382**に対応する売上高と購入同期に気が付きます。</span><span class="sxs-lookup"><span data-stu-id="22be9-208">Part way down, you can find the sales amount and sales reasons for order number **SO5382**.</span></span> <span data-ttu-id="22be9-209">この特定の注文の総計は **539.99**であり、この注文に属する購入動機には、Promotion (プロモーション)、Other (その他)、および Price (価格) が含まれています。</span><span class="sxs-lookup"><span data-stu-id="22be9-209">Grand total of this particular order is **539.99**, and the purchase reasons attributed to this order include Promotion, Other and Price.</span></span>  
  
     <span data-ttu-id="22be9-210">![多対多集計を示す Excel ワークシート](../media/ssas-m2m-excel.png "多対多集計を示す Excel ワークシート")</span><span class="sxs-lookup"><span data-stu-id="22be9-210">![Excel worksheet showing many-to-many aggregations](../media/ssas-m2m-excel.png "Excel worksheet showing many-to-many aggregations")</span></span>  
  
     <span data-ttu-id="22be9-211">この注文に対応する Sales Amount (売上高) が正確に計算され、注文全体で **539.99** であることがわかります。</span><span class="sxs-lookup"><span data-stu-id="22be9-211">Notice that the Sales Amount is correctly calculated for the order; it is **539.99** for the entire order.</span></span> <span data-ttu-id="22be9-212">動機ごとに **539.99** が示されていますが、3 つの値すべてに対してこの値が合計されて総合計を誤って膨張させることはありません。</span><span class="sxs-lookup"><span data-stu-id="22be9-212">Although **539.99** is indicated for each reason, that value is not summed for all three reasons, erroneously inflating our grand total.</span></span>  
  
     <span data-ttu-id="22be9-213">各購入動機の下で、最初に売上高が配置されているのはなぜでしょうか。</span><span class="sxs-lookup"><span data-stu-id="22be9-213">Why put a sales amount under each sales reason in the first place?</span></span> <span data-ttu-id="22be9-214">そのように配置することにより、各動機に適用できる売上高を特定できるからです。</span><span class="sxs-lookup"><span data-stu-id="22be9-214">The answer is that it allows us to identify the amount of sales we can attribute to each reason.</span></span>  
  
5.  <span data-ttu-id="22be9-215">ワークシートの下端までスクロールします。</span><span class="sxs-lookup"><span data-stu-id="22be9-215">Scroll to the bottom of the worksheet.</span></span> <span data-ttu-id="22be9-216">他の理由、および総計と比較すると、顧客の購入にとって最も重要な動機が Price (価格) であることがわかります。</span><span class="sxs-lookup"><span data-stu-id="22be9-216">It is now easy to see that Price is the most important reason for customer purchases, relative to other reasons as well as the grand total.</span></span>  
  
     <span data-ttu-id="22be9-217">![多対多内の合計を示す Excel ブック](../media/ssas-m2m-excelgrandtotal.png "多対多内の合計を示す Excel ブック")</span><span class="sxs-lookup"><span data-stu-id="22be9-217">![Excel workbook showing totals in many-to-many](../media/ssas-m2m-excelgrandtotal.png "Excel workbook showing totals in many-to-many")</span></span>  
  
#### <a name="tips-for-handling-unexpected-query-results"></a><span data-ttu-id="22be9-218">予期しないクエリ結果を処理するためのヒント</span><span class="sxs-lookup"><span data-stu-id="22be9-218">Tips for handling unexpected query results</span></span>  
  
1.  <span data-ttu-id="22be9-219">クエリで意味のある結果を返さない、カウントのような中間メジャー グループ内のメジャーを非表示にします。</span><span class="sxs-lookup"><span data-stu-id="22be9-219">Hide measures in the intermediate measure group, such as the count, that do not return meaningful results in a query.</span></span> <span data-ttu-id="22be9-220">この結果、ユーザーが意味のあるデータを作成する目的で集計などを使用することを防止できます。</span><span class="sxs-lookup"><span data-stu-id="22be9-220">This prevents people from trying to use aggregations producing meaningless data.</span></span> <span data-ttu-id="22be9-221">メジャーを非表示にするには、ディメンション デザイナー内の属性で **Visibility** (表示) を **False** に設定します。</span><span class="sxs-lookup"><span data-stu-id="22be9-221">To hide a measure, set **Visibility** to **False** on the attribute in dimension designer.</span></span>  
  
2.  <span data-ttu-id="22be9-222">実行しようとする分析操作に役立つ一部のメジャーとディメンションを使用するために、パースペクティブを作成します。</span><span class="sxs-lookup"><span data-stu-id="22be9-222">Create perspectives to use a subset of measures and dimensions that support the analytical experience you want to provide.</span></span> <span data-ttu-id="22be9-223">キューブに含まれている多くのメジャー グループやディメンションは、あらゆる状況で互いに密接に関連するわけではありません。</span><span class="sxs-lookup"><span data-stu-id="22be9-223">Possibly, a cube that contains many measure groups and dimensions do not work well together in all cases.</span></span> <span data-ttu-id="22be9-224">組み合わせて使用することを意図しているディメンションとメジャー グループを特定することで、予測可能性の高い結果を生成できます。</span><span class="sxs-lookup"><span data-stu-id="22be9-224">By isolating the dimensions and measure groups that you intend to be used together, you ensure a more predictable outcome.</span></span>  
  
3.  <span data-ttu-id="22be9-225">モデルを変更した後、必ず配置と再接続を行ってください。</span><span class="sxs-lookup"><span data-stu-id="22be9-225">Always remember to deploy and reconnect after changing a model.</span></span> <span data-ttu-id="22be9-226">Excel で、リボンの [ピボットテーブル ツール] にある [更新] ボタンを使用します。</span><span class="sxs-lookup"><span data-stu-id="22be9-226">In Excel, use the Refresh button on the PivotTable Analyze ribbon.</span></span>  
  
4.  <span data-ttu-id="22be9-227">複数の多対多リレーションシップで、リンク メジャー グループを使用することは避けてください。特に、これらのリレーションシップが異なるキューブ内に存在する場合です。</span><span class="sxs-lookup"><span data-stu-id="22be9-227">Avoid using linked measure groups in multiple many-to-many relationships, especially when those relationships are in different cubes.</span></span> <span data-ttu-id="22be9-228">このような方法で使用すると、あいまいな集計になります。</span><span class="sxs-lookup"><span data-stu-id="22be9-228">Doing so can result in ambiguous aggregations.</span></span> <span data-ttu-id="22be9-229">詳細については、「 [多対多リレーションシップを含むキューブでリンク メジャーの値が不適切](https://social.technet.microsoft.com/wiki/contents/articles/22911.incorrect-amounts-for-linked-measures-in-cubes-containing-many-to-many-relationships-ssas-troubleshooting.aspx)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="22be9-229">For more information, see [Incorrect Amounts for Linked Measures in Cubes containing Many-to-Many Relationships](https://social.technet.microsoft.com/wiki/contents/articles/22911.incorrect-amounts-for-linked-measures-in-cubes-containing-many-to-many-relationships-ssas-troubleshooting.aspx).</span></span>  
  
##  <a name="learn-more"></a><a name="bkmk_Learn"></a><span data-ttu-id="22be9-230">詳細情報</span><span class="sxs-lookup"><span data-stu-id="22be9-230">Learn more</span></span>  
 <span data-ttu-id="22be9-231">以下のリンクを使用して、この内容を習得するのに役立つ詳細情報を参照してください。</span><span class="sxs-lookup"><span data-stu-id="22be9-231">Use the following links to get additional information that helps you master the concepts.</span></span>  
  
 [<span data-ttu-id="22be9-232">Analysis Services で多対多ディメンションを定義する方法</span><span class="sxs-lookup"><span data-stu-id="22be9-232">How do I define a many-to-many dimension in Analysis Services</span></span>](../lesson-5-3-defining-a-many-to-many-relationship.md)  
  
 [<span data-ttu-id="22be9-233">多対多の回転 2.0</span><span class="sxs-lookup"><span data-stu-id="22be9-233">The many-to-many Revolution 2.0</span></span>](https://go.microsoft.com/fwlink/?LinkId=324760)  
  
 [<span data-ttu-id="22be9-234">チュートリアル : SQL Server Analysis Services を対象とする多対多ディメンションの例</span><span class="sxs-lookup"><span data-stu-id="22be9-234">Tutorial: Many-to-many dimension example for SQL Server Analysis Services</span></span>](https://go.microsoft.com/fwlink/?LinkId=324761)  
  
## <a name="see-also"></a><span data-ttu-id="22be9-235">参照</span><span class="sxs-lookup"><span data-stu-id="22be9-235">See Also</span></span>  
 <span data-ttu-id="22be9-236">[ディメンションのリレーションシップ](../multidimensional-models-olap-logical-cube-objects/dimension-relationships.md) </span><span class="sxs-lookup"><span data-stu-id="22be9-236">[Dimension Relationships](../multidimensional-models-olap-logical-cube-objects/dimension-relationships.md) </span></span>  
 <span data-ttu-id="22be9-237">[Analysis Services 多次元モデリングチュートリアル用のサンプルデータおよびプロジェクトのインストール](../install-sample-data-and-projects.md) </span><span class="sxs-lookup"><span data-stu-id="22be9-237">[Install Sample Data and Projects for the Analysis Services Multidimensional Modeling Tutorial](../install-sample-data-and-projects.md) </span></span>  
 <span data-ttu-id="22be9-238">[Analysis Services プロジェクト &#40;SSDT&#41;に配置する](deploy-analysis-services-projects-ssdt.md) </span><span class="sxs-lookup"><span data-stu-id="22be9-238">[Deploy Analysis Services Projects &#40;SSDT&#41;](deploy-analysis-services-projects-ssdt.md) </span></span>  
 [<span data-ttu-id="22be9-239">多次元モデルのパースペクティブ</span><span class="sxs-lookup"><span data-stu-id="22be9-239">Perspectives in Multidimensional Models</span></span>](perspectives-in-multidimensional-models.md)  
  
  
