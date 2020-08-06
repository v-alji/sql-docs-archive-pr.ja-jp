---
title: 緩やかに変化するディメンション ウィザードを使用して出力を構成する | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Slowly Changing Dimension transformation
- slowly changing dimensions
- Slowly Changing Dimension Wizard
ms.assetid: da111731-1ffa-49b9-bcaa-3c93fd0eb619
author: chugugrace
ms.author: chugu
ms.openlocfilehash: f6ec3dfb34de8eb7e20b255ce485ee506f070749
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642206"
---
# <a name="configure-outputs-using-the-slowly-changing-dimension-wizard"></a><span data-ttu-id="e01d9-102">緩やかに変化するディメンション ウィザードを使用して出力を構成する</span><span class="sxs-lookup"><span data-stu-id="e01d9-102">Configure Outputs Using the Slowly Changing Dimension Wizard</span></span>
  <span data-ttu-id="e01d9-103">緩やかに変化するディメンション ウィザードは、緩やかに変化するディメンションの変換用のエディターとして機能します。</span><span class="sxs-lookup"><span data-stu-id="e01d9-103">The Slowly Changing Dimension Wizard functions as the editor for the Slowly Changing Dimension transformation.</span></span> <span data-ttu-id="e01d9-104">緩やかに変化するディメンションのデータのデータ フローを構築および構成する作業は、複雑なタスクになる場合があります。</span><span class="sxs-lookup"><span data-stu-id="e01d9-104">Building and configuring the data flow for slowly changing dimension data can be a complex task.</span></span> <span data-ttu-id="e01d9-105">緩やかに変化するディメンション ウィザードを使用すると、列のマッピング、ビジネス キーの列の選択、列の変化する属性の設定、および推定ディメンション メンバー サポートの構成などの手順の指針が示され、これにより、最も簡単な方法で、緩やかに変化するディメンションの変換出力のデータ フローを構築できます。</span><span class="sxs-lookup"><span data-stu-id="e01d9-105">The Slowly Changing Dimension Wizard offers the simplest method of building the data flow for the Slowly Changing Dimension transformation outputs by guiding you through the steps of mapping columns, selecting business key columns, setting column change attributes, and configuring support for inferred dimension members.</span></span>

 <span data-ttu-id="e01d9-106">ディメンション テーブルで、ビジネス キーの列を少なくとも 1 つ選択し、入力列にマップする必要があります。</span><span class="sxs-lookup"><span data-stu-id="e01d9-106">You must choose at least one business key column in the dimension table and map it to an input column.</span></span> <span data-ttu-id="e01d9-107">ビジネス キーの値は、変換元のレコードをディメンション テーブルのレコードにリンクします。</span><span class="sxs-lookup"><span data-stu-id="e01d9-107">The value of the business key links a record in the source to a record in the dimension table.</span></span> <span data-ttu-id="e01d9-108">変換はこのマッピングを使用してディメンション テーブルのレコードを検索し、レコードが新しいものか変更されたものかを判断します。</span><span class="sxs-lookup"><span data-stu-id="e01d9-108">The transformation uses this mapping to locate the record in the dimension table and to determine whether a record is new or changing.</span></span> <span data-ttu-id="e01d9-109">通常、変換元の主キーがビジネス キーとなりますが、レコードを一意で識別し、値が変更されない限り、代替キーを使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="e01d9-109">The business key is typically the primary key in the source, but it can be an alternate key as long as it uniquely identifies a record and its value does not change.</span></span> <span data-ttu-id="e01d9-110">複数の列から成る複合キーをビジネス キーとすることもできます。</span><span class="sxs-lookup"><span data-stu-id="e01d9-110">The business key can also be a composite key, consisting of multiple columns.</span></span> <span data-ttu-id="e01d9-111">ディメンション テーブルの主キーは、通常、代理キーです。つまり、ID 列、またはスクリプトなどのカスタム ソリューションによって自動的に生成された数値です。</span><span class="sxs-lookup"><span data-stu-id="e01d9-111">The primary key in the dimension table is usually a surrogate key, which means a numeric value generated automatically by an identity column or by a custom solution such as a script.</span></span>

 <span data-ttu-id="e01d9-112">緩やかに変化するディメンション ウィザードを実行するには、変換元と緩やかに変化するディメンション変換をあらかじめデータ フローに追加し、変換元の出力を緩やかに変化するディメンションの変換入力に連結しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="e01d9-112">Before you can run the Slowly Changing Dimension Wizard, you must add a source and a Slowly Changing Dimension transformation to the data flow, and then connect the output from the source to the input of the Slowly Changing Dimension transformation.</span></span> <span data-ttu-id="e01d9-113">必要に応じて、データ フローで、データ ソースと緩やかに変化するディメンションの変換との間に、他の変換を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="e01d9-113">Optionally, the data flow can include other transformations between the data source and the Slowly Changing Dimension transformation.</span></span>

 <span data-ttu-id="e01d9-114">緩やかに変化するディメンション ウィザードを [!INCLUDE[ssIS](../../../includes/ssis-md.md)] デザイナーで開くには、緩やかに変化するディメンションの変換をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="e01d9-114">To open the Slowly Changing Dimension Wizard in [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer, double-click the Slowly Changing Dimension transformation.</span></span>

## <a name="creating-slowly-changing-dimension-outputs"></a><span data-ttu-id="e01d9-115">緩やかに変化するディメンションの出力の作成</span><span class="sxs-lookup"><span data-stu-id="e01d9-115">Creating Slowly Changing Dimension Outputs</span></span>

#### <a name="to-create-slowly-changing-dimension-transformation-outputs"></a><span data-ttu-id="e01d9-116">緩やかに変化するディメンションの変換出力を作成するには</span><span class="sxs-lookup"><span data-stu-id="e01d9-116">To create Slowly Changing Dimension transformation outputs</span></span>

1.  <span data-ttu-id="e01d9-117">更新するディメンション テーブルが含まれているデータ ソースにアクセスするための、接続マネージャーを選択します。</span><span class="sxs-lookup"><span data-stu-id="e01d9-117">Choose the connection manager to access the data source that contains the dimension table that you want to update.</span></span>

     <span data-ttu-id="e01d9-118">パッケージに含まれている接続マネージャーの一覧から選択できます。</span><span class="sxs-lookup"><span data-stu-id="e01d9-118">You can select from a list of connection managers that the package includes.</span></span>

2.  <span data-ttu-id="e01d9-119">更新するディメンション テーブルまたはビューを選択します。</span><span class="sxs-lookup"><span data-stu-id="e01d9-119">Choose the dimension table or view you want to update.</span></span>

     <span data-ttu-id="e01d9-120">テーブルまたはビューは、接続マネージャーを選択した後でデータ ソースから選択できます。</span><span class="sxs-lookup"><span data-stu-id="e01d9-120">After you select the connection manager, you can select the table or view from the data source.</span></span>

3.  <span data-ttu-id="e01d9-121">列のキー属性を設定し、入力列をディメンション テーブル内の列にマップします。</span><span class="sxs-lookup"><span data-stu-id="e01d9-121">Set key attributes on columns and map input columns to columns in the dimension table.</span></span>

     <span data-ttu-id="e01d9-122">ディメンション テーブルで、ビジネス キーの列を少なくとも 1 つ選択し、入力列にマップする必要があります。</span><span class="sxs-lookup"><span data-stu-id="e01d9-122">You must choose at least one business key column in the dimension table and map it to an input column.</span></span> <span data-ttu-id="e01d9-123">他の入力列は、非キー マッピングとしてディメンション テーブル内の列にマップできます。</span><span class="sxs-lookup"><span data-stu-id="e01d9-123">Other input columns can be mapped to columns in the dimension table as non-key mappings.</span></span>

4.  <span data-ttu-id="e01d9-124">各列に対し、変更の種類を選択します。</span><span class="sxs-lookup"><span data-stu-id="e01d9-124">Choose the change type for each column.</span></span>

    -   <span data-ttu-id="e01d9-125">**[変化する属性]** は、レコード内の既存の値を上書きします。</span><span class="sxs-lookup"><span data-stu-id="e01d9-125">**Changing attribute** overwrites existing values in records.</span></span>

    -   <span data-ttu-id="e01d9-126">**[履歴属性]** は、既存のレコードを更新せず、新しいレコードを作成します。</span><span class="sxs-lookup"><span data-stu-id="e01d9-126">**Historical attribute** creates new records instead of updating existing records.</span></span>

    -   <span data-ttu-id="e01d9-127">**[固定属性]** は、列の値は変更できないことを示します。</span><span class="sxs-lookup"><span data-stu-id="e01d9-127">**Fixed attribute** indicates that the column value must not change.</span></span>

5.  <span data-ttu-id="e01d9-128">固定属性および変化する属性のオプションを設定します。</span><span class="sxs-lookup"><span data-stu-id="e01d9-128">Set fixed and changing attribute options.</span></span>

     <span data-ttu-id="e01d9-129">列の変化の種類に **[固定属性]** を使用するように構成した場合、これらの列で変更が検出されたときに、緩やかに変化するディメンションの変換が失敗するかどうかを指定できます。</span><span class="sxs-lookup"><span data-stu-id="e01d9-129">If you configure columns to use the **Fixed attribute** change type, you can specify whether the Slowly Changing Dimension transformation fails when changes are detected in these columns.</span></span> <span data-ttu-id="e01d9-130">列の変化の種類に **[変化する属性]** を使用するように構成した場合、古いレコードを含め、一致するすべてのレコードを更新するかどうかを指定できます。</span><span class="sxs-lookup"><span data-stu-id="e01d9-130">If you configure columns to use the **Changing attribute** change type, you can specify whether all matching records, including outdated records, are updated.</span></span>

6.  <span data-ttu-id="e01d9-131">履歴属性のオプションを設定します。</span><span class="sxs-lookup"><span data-stu-id="e01d9-131">Set historical attribute options.</span></span>

     <span data-ttu-id="e01d9-132">列の変化の種類に **[履歴属性]** を使用するように構成した場合、現在のレコードと有効期限が切れたレコードとを区別する方法を選択する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e01d9-132">If you configure columns to use the **Historical attribute** change type, you must choose how to distinguish between current and expired records.</span></span> <span data-ttu-id="e01d9-133">現在の行と有効期限が切れた行を判別するには、現在の行のインジケーター列または 2 つの日付列が使用できます。</span><span class="sxs-lookup"><span data-stu-id="e01d9-133">You can use a current row indicator column or two date columns to identify current and expired rows.</span></span> <span data-ttu-id="e01d9-134">現在の行のインジケーター列を使用する場合は、現在の行には **[現在]** または **[True]** を設定し、有効期限が切れた行には **[有効期限切れ]** または **[False]** を設定できます。</span><span class="sxs-lookup"><span data-stu-id="e01d9-134">If you use the current row indicator column, you can set it to **Current**, **True** when current and **Expired,** or **False** when expired.</span></span> <span data-ttu-id="e01d9-135">また、カスタム値を入力することもできます。</span><span class="sxs-lookup"><span data-stu-id="e01d9-135">You can also enter custom values.</span></span> <span data-ttu-id="e01d9-136">開始日と終了日の 2 つの日付列を使用する場合、日付を入力するかまたはシステム変数を選択してその値を使用することにより、日付列の値を設定するときに使用する日付を指定できます。</span><span class="sxs-lookup"><span data-stu-id="e01d9-136">If you use two date columns, a start date and an end date, you can specify the date to use when setting the date column values by typing a date or by selecting a system variable and then using its value.</span></span>

7.  <span data-ttu-id="e01d9-137">推定メンバーをサポートするかどうかを指定し、推定メンバー レコードが含む列を選択します。</span><span class="sxs-lookup"><span data-stu-id="e01d9-137">Specify support for inferred members and choose the columns that the inferred member record contains.</span></span>

     <span data-ttu-id="e01d9-138">ファクト テーブルにメジャーを読み込むときに、まだ存在しない推定メンバーの最小レコードを作成できます。</span><span class="sxs-lookup"><span data-stu-id="e01d9-138">When loading measures into a fact table, you can create minimal records for inferred members that do not yet exist.</span></span> <span data-ttu-id="e01d9-139">後で、意味のあるデータが使用できるようになったときに、ディメンション レコードを更新できます。</span><span class="sxs-lookup"><span data-stu-id="e01d9-139">Later, when meaningful data is available, the dimension records can be updated.</span></span> <span data-ttu-id="e01d9-140">次の種類の最小レコードを作成できます。</span><span class="sxs-lookup"><span data-stu-id="e01d9-140">The following types of minimal records can be created:</span></span>

    -   <span data-ttu-id="e01d9-141">変更の種類が設定された列がすべて NULL であるレコード。</span><span class="sxs-lookup"><span data-stu-id="e01d9-141">A record in which all columns with change types are null.</span></span>

    -   <span data-ttu-id="e01d9-142">ブール値の列により、推定メンバーであることが示されているレコード。</span><span class="sxs-lookup"><span data-stu-id="e01d9-142">A record in which a Boolean column indicates the record is an inferred member.</span></span>

8.  <span data-ttu-id="e01d9-143">緩やかに変化するディメンション ウィザードが構築した構成を確認します。</span><span class="sxs-lookup"><span data-stu-id="e01d9-143">Review the configurations that the Slowly Changing Dimension Wizard builds.</span></span> <span data-ttu-id="e01d9-144">サポートされる変更の種類に応じて、さまざまなデータ フロー コンポーネントの組み合わせがパッケージに追加されます。</span><span class="sxs-lookup"><span data-stu-id="e01d9-144">Depending on which change types are supported, different sets of data flow components are added to the package.</span></span>

     <span data-ttu-id="e01d9-145">次の図は、固定属性、変化する属性、および履歴属性の変化、推定メンバー、および一致するレコードへの変更をサポートする、データ フローの例を示しています。</span><span class="sxs-lookup"><span data-stu-id="e01d9-145">The following diagram shows an example of a data flow that supports fixed attribute, changing attribute, and historical attribute changes, inferred members, and changes to matching records.</span></span>

     <span data-ttu-id="e01d9-146">![緩やかに変化するディメンション ウィザードからのデータ フロー](../../media/dimensionwizard.gif "緩やかに変化するディメンション ウィザードからのデータ フロー")</span><span class="sxs-lookup"><span data-stu-id="e01d9-146">![Data flow from Slowly Changing Dimension Wizard](../../media/dimensionwizard.gif "Data flow from Slowly Changing Dimension Wizard")</span></span>

## <a name="updating-slowly-changing-dimension-outputs"></a><span data-ttu-id="e01d9-147">緩やかに変化するディメンションの出力の更新</span><span class="sxs-lookup"><span data-stu-id="e01d9-147">Updating Slowly Changing Dimension Outputs</span></span>
 <span data-ttu-id="e01d9-148">緩やかに変化するディメンションの変換出力の構成を最も簡単に更新するには、緩やかに変化するディメンション ウィザードを再実行し、ウィザード ページからプロパティを変更します。</span><span class="sxs-lookup"><span data-stu-id="e01d9-148">The simplest way to update the configuration of the Slowly Changing Dimension transformation outputs is to rerun the Slowly Changing Dimension Wizard and modify properties from the wizard pages.</span></span> <span data-ttu-id="e01d9-149">また、 **[詳細エディター]** ダイアログ ボックスまたはプログラムによっても、緩やかに変化するディメンションの変換を更新できます。</span><span class="sxs-lookup"><span data-stu-id="e01d9-149">You can also update the Slowly Changing Dimension transformation using the **Advanced Editor** dialog box or programmatically.</span></span>

## <a name="see-also"></a><span data-ttu-id="e01d9-150">参照</span><span class="sxs-lookup"><span data-stu-id="e01d9-150">See Also</span></span>
 [<span data-ttu-id="e01d9-151">緩やかに変化するディメンション変換</span><span class="sxs-lookup"><span data-stu-id="e01d9-151">Slowly Changing Dimension Transformation</span></span>](slowly-changing-dimension-transformation.md)


