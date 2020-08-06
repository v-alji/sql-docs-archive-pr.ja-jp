---
title: 親子型ディメンションの財務アカウントを作成する |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- dimensions [Analysis Services], account
- account dimensions [Analysis Services]
- adding account intelligence
- account intelligence [Analysis Services]
ms.assetid: 2ba74e81-5b4b-407e-acdf-deb2f6accf0a
author: minewiskan
ms.author: owend
ms.openlocfilehash: ba10e642425628426d9183be2b8d2c4ff751c3ef
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87714681"
---
# <a name="create-a-finance-account-of-parent-child-type-dimension"></a><span data-ttu-id="446c4-102">親子型ディメンションの財務アカウントの作成</span><span class="sxs-lookup"><span data-stu-id="446c4-102">Create a Finance Account of parent-child type Dimension</span></span>
  <span data-ttu-id="446c4-103">で [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] は、勘定科目の種類のディメンションとは、財務報告のために勘定科目のグラフを表す属性を持つディメンションです。</span><span class="sxs-lookup"><span data-stu-id="446c4-103">In [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], an account type dimension is a dimension whose attributes represent a chart of accounts for financial reporting purposes.</span></span>  
  
 <span data-ttu-id="446c4-104">勘定科目ディメンションを使用すると、勘定科目における集計動作の推移を選択的に管理できます。</span><span class="sxs-lookup"><span data-stu-id="446c4-104">An account dimension lets you selectively manage aggregation behavior across accounts over time.</span></span> <span data-ttu-id="446c4-105">また、財務データを取り扱うビジネス インテリジェンス ソリューションで一般的に発生する標準外の集計上の問題を、標準メカニズムを使用して解決できるようにもなります。</span><span class="sxs-lookup"><span data-stu-id="446c4-105">An account dimension also lets use a standard mechanism to resolve most of the nonstandard aggregation issues typically encountered in business intelligence solutions that handle financial data.</span></span> <span data-ttu-id="446c4-106">標準メカニズムがない場合、このような標準外の集計上の問題は、カスタム ロールアップ数式、計算されたメンバー、多次元式 (MDX) スクリプトなどがなければ解決できません。</span><span class="sxs-lookup"><span data-stu-id="446c4-106">If you did not have such a standard mechanism, resolving these nonstandard aggregation issues would require custom rollup formulas, calculated members, or Multidimensional Expressions (MDX) scripts.</span></span>  
  
 <span data-ttu-id="446c4-107">ディメンションを勘定科目ディメンションとして指定するには、ディメンションの `Type` プロパティを `Accounts` に設定します。</span><span class="sxs-lookup"><span data-stu-id="446c4-107">To identify a dimension as an account dimension, set the `Type` property of the dimension to `Accounts`.</span></span>  
  
## <a name="dimension-structure"></a><span data-ttu-id="446c4-108">[ディメンション構造]</span><span class="sxs-lookup"><span data-stu-id="446c4-108">Dimension Structure</span></span>  
 <span data-ttu-id="446c4-109">勘定科目ディメンションには、少なくとも次の 2 つの属性が含まれています。</span><span class="sxs-lookup"><span data-stu-id="446c4-109">An account dimension contains, at least, two attributes:</span></span>  
  
-   <span data-ttu-id="446c4-110">キー属性-勘定科目ディメンションのディメンションテーブル内の個々の勘定科目を識別する属性です。</span><span class="sxs-lookup"><span data-stu-id="446c4-110">A key attribute-an attribute that identifies individual accounts in the dimension table for the account dimension.</span></span>  
  
-   <span data-ttu-id="446c4-111">勘定科目属性-勘定科目ディメンションにおける勘定科目の階層構造を記述する親属性です。</span><span class="sxs-lookup"><span data-stu-id="446c4-111">An account attribute-a parent attribute that describes how accounts are hierarchically arranged in the account dimension.</span></span>  
  
     <span data-ttu-id="446c4-112">属性を勘定科目属性として指定するには、属性の `Type` プロパティを `Account` に設定し、`Usage` プロパティを `Parent` に設定します。</span><span class="sxs-lookup"><span data-stu-id="446c4-112">To identify an attribute as an account attribute, set the `Type` property of the attribute to `Account` and the `Usage` property to `Parent`.</span></span>  
  
 <span data-ttu-id="446c4-113">勘定科目ディメンションには、次の属性をオプションで含めることもできます。</span><span class="sxs-lookup"><span data-stu-id="446c4-113">Account dimensions can optionally contain the following attributes:</span></span>  
  
-   <span data-ttu-id="446c4-114">勘定科目の種類の属性-ディメンション内の各アカウントの勘定科目の種類を定義する属性です。</span><span class="sxs-lookup"><span data-stu-id="446c4-114">An account type attribute-an attribute that defines the account type for each account in the dimension.</span></span> <span data-ttu-id="446c4-115">勘定科目の種類の属性のメンバー名は、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のデータベースまたはプロジェクトに対して定義された勘定科目の種類にマップされ、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] によってこれらの勘定科目に対して使用される集計関数を示します。</span><span class="sxs-lookup"><span data-stu-id="446c4-115">The member names of the account type attribute map to the account types defined for the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database or project, and indicate the aggregation function used by [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] for those accounts.</span></span> <span data-ttu-id="446c4-116">単項演算子またはカスタム ロールアップ数式を使用しても、勘定科目属性の集計動作を指定することができますが、勘定科目の種類を使用すると、基になるリレーショナル データベースを変更しなくても一貫性のある動作を勘定科目一覧表に簡単に適用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="446c4-116">You can also use unary operators or custom rollup formulas to determine aggregation behavior for account attributes, but account types let you to easily apply consistent behavior to a chart of accounts without requiring changes to the underlying relational database.</span></span>  
  
     <span data-ttu-id="446c4-117">勘定科目の種類の属性を指定するには、属性の `Type` プロパティを `AccountType` に設定します。</span><span class="sxs-lookup"><span data-stu-id="446c4-117">To identify an account type attribute, set the `Type` property of the attribute to `AccountType`.</span></span>  
  
-   <span data-ttu-id="446c4-118">アカウント名属性-レポートのために使用される属性です。</span><span class="sxs-lookup"><span data-stu-id="446c4-118">An account name attribute-an attribute that is used for reporting purposes.</span></span> <span data-ttu-id="446c4-119">勘定科目名属性を指定するには、属性の `Type` プロパティを `AccountName` に設定します。</span><span class="sxs-lookup"><span data-stu-id="446c4-119">You identify an account name attribute by setting the `Type` property of the attribute to `AccountName`.</span></span>  
  
-   <span data-ttu-id="446c4-120">勘定科目番号属性-レポートのために使用される属性です。</span><span class="sxs-lookup"><span data-stu-id="446c4-120">An account number attribute-an attribute that is used for reporting purposes.</span></span> <span data-ttu-id="446c4-121">勘定科目番号属性を指定するには、属性の `Type` プロパティを `AccountNumber` に設定します。</span><span class="sxs-lookup"><span data-stu-id="446c4-121">You identify an account number attribute by setting the `Type` property of the attribute to `AccountNumber`.</span></span>  
  
 <span data-ttu-id="446c4-122">属性の種類の詳細については、「 [属性の種類の構成](attribute-properties-configure-attribute-types.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="446c4-122">For more information about attribute types, see [Configure Attribute Types](attribute-properties-configure-attribute-types.md).</span></span>  
  
## <a name="adding-account-intelligence-with-the-business-intelligence-wizard"></a><span data-ttu-id="446c4-123">ビジネス インテリジェンス ウィザードを使用した勘定科目インテリジェンスの追加</span><span class="sxs-lookup"><span data-stu-id="446c4-123">Adding Account Intelligence with the Business Intelligence Wizard</span></span>  
 <span data-ttu-id="446c4-124">勘定科目ディメンションを定義し、定義したディメンションをキューブに追加したら、ビジネス インテリジェンス ウィザードを使用して、勘定科目の種類の特定とマップなどの勘定科目インテリジェンス機能をディメンションに追加することができます。</span><span class="sxs-lookup"><span data-stu-id="446c4-124">After you have defined an account dimension and added that dimension to a cube, you can use the Business Intelligence Wizard to adding account intelligence functionality, such as identifying and mapping account types, to the dimension.</span></span> <span data-ttu-id="446c4-125">詳細については、「 [ディメンションへの勘定科目インテリジェンスの追加](bi-wizard-add-account-intelligence-to-a-dimension.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="446c4-125">For more information, see [Add Account Intelligence to a Dimension](bi-wizard-add-account-intelligence-to-a-dimension.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="446c4-126">参照</span><span class="sxs-lookup"><span data-stu-id="446c4-126">See Also</span></span>  
 <span data-ttu-id="446c4-127">[属性と属性階層](../multidimensional-models-olap-logical-dimension-objects/attributes-and-attribute-hierarchies.md) </span><span class="sxs-lookup"><span data-stu-id="446c4-127">[Attributes and Attribute Hierarchies](../multidimensional-models-olap-logical-dimension-objects/attributes-and-attribute-hierarchies.md) </span></span>  
 <span data-ttu-id="446c4-128">[ビジネスインテリジェンスウィザードの F1 ヘルプ](../business-intelligence-wizard-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="446c4-128">[Business Intelligence Wizard F1 Help](../business-intelligence-wizard-f1-help.md) </span></span>  
 [<span data-ttu-id="446c4-129">ディメンションの種類</span><span class="sxs-lookup"><span data-stu-id="446c4-129">Dimension Types</span></span>](../multidimensional-models-olap-logical-dimension-objects/database-dimension-properties-types.md)  
  
  
