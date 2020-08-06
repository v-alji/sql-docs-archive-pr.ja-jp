---
title: '[DQS クレンジング変換エディター] ダイアログボックス |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.ssdqs.designer.cleansing.f1
- SQL12.SSDQS.DESIGNER.DQCONNECTION.F1
ms.assetid: 07e79641-71ee-45d0-a9ba-ed6f9f68f333
author: chugugrace
ms.author: chugu
ms.openlocfilehash: e97cd138bb17ce3cfe476496e5bc576875728224
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632022"
---
# <a name="dqs-cleansing-transformation-editor-dialog-box"></a><span data-ttu-id="a9a5a-102">[DQS クレンジング変換エディター] ダイアログ ボックス</span><span class="sxs-lookup"><span data-stu-id="a9a5a-102">DQS Cleansing Transformation Editor Dialog Box</span></span>
  <span data-ttu-id="a9a5a-103">**[DQS クレンジング変換エディター]** ダイアログ ボックスを使用すると、Data Quality Services (DQS) を使用してデータを修正できます。</span><span class="sxs-lookup"><span data-stu-id="a9a5a-103">Use the **DQS Cleansing Transformation Editor** dialog box to correct data using Data Quality Services (DQS).</span></span> <span data-ttu-id="a9a5a-104">詳細については、「 [Data Quality Services の概念](../../2014/data-quality-services/data-quality-services-concepts.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a9a5a-104">For more information, see [Data Quality Services Concepts](../../2014/data-quality-services/data-quality-services-concepts.md).</span></span>  
  
 <span data-ttu-id="a9a5a-105">変換の詳細については、「 [DQS クレンジング変換](data-flow/transformations/dqs-cleansing-transformation.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a9a5a-105">To learn more about the transformation, see [DQS Cleansing Transformation](data-flow/transformations/dqs-cleansing-transformation.md).</span></span>  
  
 <span data-ttu-id="a9a5a-106">**目的に合ったトピックをクリックしてください**</span><span class="sxs-lookup"><span data-stu-id="a9a5a-106">**What do you want to do?**</span></span>  
  
-   [<span data-ttu-id="a9a5a-107">DQS クレンジング変換エディターを開く</span><span class="sxs-lookup"><span data-stu-id="a9a5a-107">Open the DQS Cleansing Transformation Editor</span></span>](#open)  
  
-   <span data-ttu-id="a9a5a-108">[[接続マネージャー] タブのオプションの設定](#connection)</span><span class="sxs-lookup"><span data-stu-id="a9a5a-108">[Set options on the Connection Manager tab](#connection)</span></span>  
  
-   <span data-ttu-id="a9a5a-109">[[マッピング] タブのオプションの設定](#mapping)</span><span class="sxs-lookup"><span data-stu-id="a9a5a-109">[Set options on the Mapping tab](#mapping)</span></span>  
  
-   <span data-ttu-id="a9a5a-110">[[詳細設定] タブのオプションの設定](#advanced)</span><span class="sxs-lookup"><span data-stu-id="a9a5a-110">[Set options on the Advanced tab](#advanced)</span></span>  
  
-   <span data-ttu-id="a9a5a-111">[[DQS クレンジング接続マネージャー] ダイアログ ボックスのオプションの設定](#manager)</span><span class="sxs-lookup"><span data-stu-id="a9a5a-111">[Set the options in the DQS Cleansing Connection Manager dialog box](#manager)</span></span>  
  
##  <a name="open-the-dqs-cleansing-transformation-editor"></a><a name="open"></a><span data-ttu-id="a9a5a-112">DQS クレンジング変換エディターを開く</span><span class="sxs-lookup"><span data-stu-id="a9a5a-112">Open the DQS Cleansing Transformation Editor</span></span>  
  
1.  <span data-ttu-id="a9a5a-113">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] で、DQS クレンジング変換を [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]パッケージに追加します。</span><span class="sxs-lookup"><span data-stu-id="a9a5a-113">Add the DQS Cleansing Transformation to [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] package, in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span>  
  
2.  <span data-ttu-id="a9a5a-114">コンポーネントを右クリックし、 **[編集]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a9a5a-114">Right-click the component and then click **Edit**.</span></span>  
  
##  <a name="set-options-on-the-connection-manager-tab"></a><a name="connection"></a> <span data-ttu-id="a9a5a-115">[接続マネージャー] タブのオプションの設定</span><span class="sxs-lookup"><span data-stu-id="a9a5a-115">Set options on the Connection Manager tab</span></span>  
 <span data-ttu-id="a9a5a-116">**[データ品質接続マネージャー]**</span><span class="sxs-lookup"><span data-stu-id="a9a5a-116">**Data quality connection manager**</span></span>  
 <span data-ttu-id="a9a5a-117">既存の DQS 接続マネージャーを一覧から選択するか、 **[新規作成]** をクリックして新しい接続を作成します。</span><span class="sxs-lookup"><span data-stu-id="a9a5a-117">Select an existing DQS connection manager from the list, or create a new connection by clicking **New**.</span></span>  
  
 <span data-ttu-id="a9a5a-118">**[新規作成]**</span><span class="sxs-lookup"><span data-stu-id="a9a5a-118">**New**</span></span>  
 <span data-ttu-id="a9a5a-119">**[DQS クレンジング接続マネージャー]** ダイアログ ボックスを使用して、新しい接続マネージャーを作成します。</span><span class="sxs-lookup"><span data-stu-id="a9a5a-119">Create a new connection manager by using the **DQS Cleansing Connection Manager** dialog box.</span></span> <span data-ttu-id="a9a5a-120">「 [[DQS クレンジング接続マネージャー] ダイアログ ボックスのオプションの設定](#manager)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a9a5a-120">See [Set the options in the DQS Cleansing Connection Manager dialog box](#manager)</span></span>  
  
 <span data-ttu-id="a9a5a-121">**[データ品質ナレッジ ベース]**</span><span class="sxs-lookup"><span data-stu-id="a9a5a-121">**Data Quality Knowledge Base**</span></span>  
 <span data-ttu-id="a9a5a-122">接続されたデータ ソースの既存の DQS ナレッジ ベースを選択します。</span><span class="sxs-lookup"><span data-stu-id="a9a5a-122">Select an existing DQS knowledge base for the connected data source.</span></span> <span data-ttu-id="a9a5a-123">DQS サポート技術情報の詳細については、「 [DQS のナレッジ ベースとドメイン](../../2014/data-quality-services/dqs-knowledge-bases-and-domains.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a9a5a-123">For more information about the DQS knowledge base, see [DQS Knowledge Bases and Domains](../../2014/data-quality-services/dqs-knowledge-bases-and-domains.md).</span></span>  
  
 <span data-ttu-id="a9a5a-124">**接続を暗号化する**</span><span class="sxs-lookup"><span data-stu-id="a9a5a-124">**Encrypt connection**</span></span>  
 <span data-ttu-id="a9a5a-125">DQS サーバーとの間のデータ転送を暗号化するために、接続を暗号化するかどうかを指定し [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="a9a5a-125">specify whether to encrypt the connection, in order to encrypt the data transfer between the DQS Server and [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="a9a5a-126">**[使用できるドメイン]**</span><span class="sxs-lookup"><span data-stu-id="a9a5a-126">**Available domains**</span></span>  
 <span data-ttu-id="a9a5a-127">選択されたナレッジ ベースで使用できるドメインを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="a9a5a-127">Lists the available domains for the selected knowledge base.</span></span> <span data-ttu-id="a9a5a-128">ドメインには、単一ドメインと、2 つ以上の単一ドメインが含まれた複合ドメインの 2 種類があります。</span><span class="sxs-lookup"><span data-stu-id="a9a5a-128">There are two types of domains: single domains, and composite domains that contain two or more single domains.</span></span>  
  
 <span data-ttu-id="a9a5a-129">複合ドメインに列をマップする方法については、「 [複合ドメインへの列のマップ](data-flow/transformations/map-columns-to-composite-domains.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a9a5a-129">For information on how to map columns to composite domains, see [Map Columns to Composite Domains](data-flow/transformations/map-columns-to-composite-domains.md).</span></span>  
  
 <span data-ttu-id="a9a5a-130">ドメインの詳細については、「 [DQS のナレッジ ベースとドメイン](../../2014/data-quality-services/dqs-knowledge-bases-and-domains.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a9a5a-130">For more information about domains, see [DQS Knowledge Bases and Domains](../../2014/data-quality-services/dqs-knowledge-bases-and-domains.md).</span></span>  
  
 <span data-ttu-id="a9a5a-131">**エラー出力の構成**</span><span class="sxs-lookup"><span data-stu-id="a9a5a-131">**Configure Error Output**</span></span>  
 <span data-ttu-id="a9a5a-132">行レベルのエラーを処理する方法を指定します。</span><span class="sxs-lookup"><span data-stu-id="a9a5a-132">Specify how to handle row-level errors.</span></span> <span data-ttu-id="a9a5a-133">接続されたデータ ソースのデータを変換で修正する際には、予期しないデータ値や検証制約が原因でエラーが発生することがあります。</span><span class="sxs-lookup"><span data-stu-id="a9a5a-133">Errors can occur when the transformation corrects data from the connected data source, due to unexpected data values or validation constraints.</span></span>  
  
 <span data-ttu-id="a9a5a-134">有効な値は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="a9a5a-134">The following are the valid values:</span></span>  
  
-   <span data-ttu-id="a9a5a-135">**[エラー コンポーネント]**: 変換に失敗したこと、およびデータが Data Quality Services データベースに挿入されていないことを示します。</span><span class="sxs-lookup"><span data-stu-id="a9a5a-135">**Fail Component**, which indicates that the transformation fails and the input data is not inserted into the Data Quality Services database.</span></span> <span data-ttu-id="a9a5a-136">これが既定値です。</span><span class="sxs-lookup"><span data-stu-id="a9a5a-136">This is the default value.</span></span>  
  
-   <span data-ttu-id="a9a5a-137">**[行のリダイレクト]**: 入力データが Data Quality Services データベースに挿入されていないために、エラー出力にリダイレクトされることを示します。</span><span class="sxs-lookup"><span data-stu-id="a9a5a-137">**Redirect Row**, which indicates that the input data is not inserted into the Data Quality Services database and is redirected to the error output.</span></span>  
  
##  <a name="set-options-on-the-mapping-tab"></a><a name="mapping"></a><span data-ttu-id="a9a5a-138">[マッピング] タブのオプションの設定</span><span class="sxs-lookup"><span data-stu-id="a9a5a-138">Set options on the Mapping tab</span></span>  
 <span data-ttu-id="a9a5a-139">複合ドメインに列をマップする方法については、「 [複合ドメインへの列のマップ](data-flow/transformations/map-columns-to-composite-domains.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a9a5a-139">For information on how to map columns to composite domains, see [Map Columns to Composite Domains](data-flow/transformations/map-columns-to-composite-domains.md).</span></span>  
  
 <span data-ttu-id="a9a5a-140">**使用できる入力列**</span><span class="sxs-lookup"><span data-stu-id="a9a5a-140">**Available Input Columns**</span></span>  
 <span data-ttu-id="a9a5a-141">接続されたデータ ソースの列を一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="a9a5a-141">Lists the columns from the connected data source.</span></span> <span data-ttu-id="a9a5a-142">修正するデータを含む 1 つまたは複数の列を選択します。</span><span class="sxs-lookup"><span data-stu-id="a9a5a-142">Select one or more columns that contain data that you want to correct.</span></span>  
  
 <span data-ttu-id="a9a5a-143">**入力列**</span><span class="sxs-lookup"><span data-stu-id="a9a5a-143">**Input Column**</span></span>  
 <span data-ttu-id="a9a5a-144">**[使用できる入力列]** 領域で選択した入力列を一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="a9a5a-144">Lists an input column that you selected in the **Available Input Columns** area.</span></span>  
  
 <span data-ttu-id="a9a5a-145">**[ドメイン]**</span><span class="sxs-lookup"><span data-stu-id="a9a5a-145">**Domain**</span></span>  
 <span data-ttu-id="a9a5a-146">入力列にマップするドメインを選択します。</span><span class="sxs-lookup"><span data-stu-id="a9a5a-146">Select a domain to map to the input column.</span></span>  
  
 <span data-ttu-id="a9a5a-147">**[ソースの別名]**</span><span class="sxs-lookup"><span data-stu-id="a9a5a-147">**Source Alias**</span></span>  
 <span data-ttu-id="a9a5a-148">元の列値を含むソース列を一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="a9a5a-148">Lists the source column that contains the original column value.</span></span>  
  
 <span data-ttu-id="a9a5a-149">列名を変更するフィールドをクリックしてください。</span><span class="sxs-lookup"><span data-stu-id="a9a5a-149">Click in the field to modify the column name.</span></span>  
  
 <span data-ttu-id="a9a5a-150">**[出力の別名]**</span><span class="sxs-lookup"><span data-stu-id="a9a5a-150">**Output Alias**</span></span>  
 <span data-ttu-id="a9a5a-151">**DQS クレンジング変換**によって出力された列を一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="a9a5a-151">Lists the column that is outputted by the **DQS Cleansing Transformation**.</span></span> <span data-ttu-id="a9a5a-152">この列には、元の列値または修正後の値が含まれます。</span><span class="sxs-lookup"><span data-stu-id="a9a5a-152">The column contains the original column value or the corrected value.</span></span>  
  
 <span data-ttu-id="a9a5a-153">列名を変更するフィールドをクリックしてください。</span><span class="sxs-lookup"><span data-stu-id="a9a5a-153">Click in the field to modify the column name.</span></span>  
  
 <span data-ttu-id="a9a5a-154">**[状態の別名]**</span><span class="sxs-lookup"><span data-stu-id="a9a5a-154">**Status Alias**</span></span>  
 <span data-ttu-id="a9a5a-155">修正されたデータの状態情報を含む列を一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="a9a5a-155">Lists the column that contains status information for the corrected data.</span></span> <span data-ttu-id="a9a5a-156">列名を変更するフィールドをクリックしてください。</span><span class="sxs-lookup"><span data-stu-id="a9a5a-156">Click in the field to modify the column name.</span></span>  
  
##  <a name="set-options-on-the-advanced-tab"></a><a name="advanced"></a><span data-ttu-id="a9a5a-157">[詳細設定] タブのオプションの設定</span><span class="sxs-lookup"><span data-stu-id="a9a5a-157">Set options on the Advanced tab</span></span>  
 <span data-ttu-id="a9a5a-158">**[出力の標準化]**</span><span class="sxs-lookup"><span data-stu-id="a9a5a-158">**Standardize output**</span></span>  
 <span data-ttu-id="a9a5a-159">ドメインで定義されている出力形式に基づいて標準化された形式でデータを出力するかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="a9a5a-159">Indicate whether to output the data in the standardized format based on the output format defined for domains.</span></span> <span data-ttu-id="a9a5a-160">標準化された形式の詳細については、「 [データ クレンジング](../../2014/data-quality-services/data-cleansing.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a9a5a-160">For more information about standardized format, see [Data Cleansing](../../2014/data-quality-services/data-cleansing.md).</span></span>  
  
 <span data-ttu-id="a9a5a-161">**Italic**</span><span class="sxs-lookup"><span data-stu-id="a9a5a-161">**Confidence**</span></span>  
 <span data-ttu-id="a9a5a-162">修正されたデータの信頼レベルを含めるかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="a9a5a-162">Indicate whether to include the confidence level for corrected data.</span></span> <span data-ttu-id="a9a5a-163">信頼レベルは、DQS の修正または候補に対する確実性の度合いを示します。</span><span class="sxs-lookup"><span data-stu-id="a9a5a-163">The confidence level indicates the extend of certainty of DQS for the correction or suggestion.</span></span> <span data-ttu-id="a9a5a-164">信頼レベルの詳細については、「 [データ クレンジング](../../2014/data-quality-services/data-cleansing.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a9a5a-164">For more information about confidence levels, see [Data Cleansing](../../2014/data-quality-services/data-cleansing.md).</span></span>  
  
 <span data-ttu-id="a9a5a-165">**理由**</span><span class="sxs-lookup"><span data-stu-id="a9a5a-165">**Reason**</span></span>  
 <span data-ttu-id="a9a5a-166">データ修正の理由を含めるかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="a9a5a-166">Indicate whether to include the reason for the data correction.</span></span>  
  
 <span data-ttu-id="a9a5a-167">**[追加されたデータ]**</span><span class="sxs-lookup"><span data-stu-id="a9a5a-167">**Appended Data**</span></span>  
 <span data-ttu-id="a9a5a-168">既存の参照データ プロバイダーから取得した追加データを出力するかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="a9a5a-168">Indicate whether to output additional data that is received from an existing reference data provider.</span></span> <span data-ttu-id="a9a5a-169">詳細については、「 [Reference Data Services in DQS](../../2014/data-quality-services/reference-data-services-in-dqs.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="a9a5a-169">For more information, see [Reference Data Services in DQS](../../2014/data-quality-services/reference-data-services-in-dqs.md).</span></span>  
  
 <span data-ttu-id="a9a5a-170">**[追加されたデータ スキーマ]**</span><span class="sxs-lookup"><span data-stu-id="a9a5a-170">**Appended Data Schema**</span></span>  
 <span data-ttu-id="a9a5a-171">データ スキーマを出力するかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="a9a5a-171">Indicate whether to output the data schema.</span></span> <span data-ttu-id="a9a5a-172">詳細については、「[参照データへのドメインまたは複合ドメインのアタッチ](../../2014/data-quality-services/attach-a-domain-or-composite-domain-to-reference-data.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a9a5a-172">For more information, see [Attach a Domain or Composite Domain to Reference Data](../../2014/data-quality-services/attach-a-domain-or-composite-domain-to-reference-data.md).</span></span>  
  
##  <a name="set-the-options-in-the-dqs-cleansing-connection-manager-dialog-box"></a><a name="manager"></a><span data-ttu-id="a9a5a-173">[DQS クレンジング接続マネージャー] ダイアログボックスのオプションの設定</span><span class="sxs-lookup"><span data-stu-id="a9a5a-173">Set the options in the DQS Cleansing Connection Manager dialog box</span></span>  
 <span data-ttu-id="a9a5a-174">**サーバー名**</span><span class="sxs-lookup"><span data-stu-id="a9a5a-174">**Server name**</span></span>  
 <span data-ttu-id="a9a5a-175">接続先の DQS サーバーの名前を選択または入力します。</span><span class="sxs-lookup"><span data-stu-id="a9a5a-175">Select or type the name of the DQS server that you want to connect to.</span></span> <span data-ttu-id="a9a5a-176">サーバーの詳細については、「 [DQS 管理](../../2014/data-quality-services/dqs-administration.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a9a5a-176">For more information about the server, see [DQS Administration](../../2014/data-quality-services/dqs-administration.md).</span></span>  
  
 <span data-ttu-id="a9a5a-177">**[接続テスト]**</span><span class="sxs-lookup"><span data-stu-id="a9a5a-177">**Test Connection**</span></span>  
 <span data-ttu-id="a9a5a-178">クリックすると、指定した接続が利用可能であることを確認できます。</span><span class="sxs-lookup"><span data-stu-id="a9a5a-178">Click to confirm that the connection that you specified is viable.</span></span>  
  
 <span data-ttu-id="a9a5a-179">次の方法で、接続領域から **[DQS クレンジング接続マネージャー]** ダイアログ ボックスを開くこともできます。</span><span class="sxs-lookup"><span data-stu-id="a9a5a-179">You can also open the **DQS Cleansing Connection Manager** dialog box from the connections area, by doing the following:</span></span>  
  
1.  <span data-ttu-id="a9a5a-180">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]で、既存の [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] プロジェクトを開くか、新しいプロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="a9a5a-180">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open an existing [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project or create a new one.</span></span>  
  
2.  <span data-ttu-id="a9a5a-181">接続領域内を右クリックし、 **[新しい接続]** をクリックして、 **[DQS]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a9a5a-181">Right-click in the connections area, click **New Connection**, and then click **DQS**.</span></span>  
  
3.  <span data-ttu-id="a9a5a-182">**[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a9a5a-182">Click **Add**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9a5a-183">参照</span><span class="sxs-lookup"><span data-stu-id="a9a5a-183">See Also</span></span>  
 [<span data-ttu-id="a9a5a-184">データ ソースにデータ品質ルールを適用する</span><span class="sxs-lookup"><span data-stu-id="a9a5a-184">Apply Data Quality Rules to Data Source</span></span>](data-flow/transformations/apply-data-quality-rules-to-data-source.md)  
  
  
