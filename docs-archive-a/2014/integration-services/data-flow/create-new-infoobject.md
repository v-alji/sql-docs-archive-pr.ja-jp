---
title: '[新しいインフォオブジェクトの作成]| Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 3587a633-1c0b-4d63-a22a-6b2b93923c3a
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 022f2d1e3fe10ae037ea379a02a18845b3a36107
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644576"
---
# <a name="create-new-infoobject"></a><span data-ttu-id="abd90-102">[新しいインフォオブジェクトの作成]</span><span class="sxs-lookup"><span data-stu-id="abd90-102">Create New InfoObject</span></span>
  <span data-ttu-id="abd90-103">SAP Netweaver BW システムで新しいインフォオブジェクトを作成するには、 **[新しいインフォオブジェクトの作成]** ダイアログ ボックスを使用します。</span><span class="sxs-lookup"><span data-stu-id="abd90-103">Use the **Create New InfoObject** dialog box to create a new InfoObject in the SAP Netweaver BW system.</span></span>  
  
 <span data-ttu-id="abd90-104">**[新しいインフォオブジェクトの作成]** ダイアログ ボックスは、 **[SAP BW 変換先エディター]** の **[接続マネージャー]** ページから開くことができます。</span><span class="sxs-lookup"><span data-stu-id="abd90-104">You can open the **Create InfoObject** dialog box from the **Connection Manager** page of the **SAP BW Destination Editor**.</span></span> <span data-ttu-id="abd90-105">SAP BW 変換先の詳細については、「 [SAP BW Destination](sap-bw-destination.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="abd90-105">To learn more about the SAP BW destination, see [SAP BW Destination](sap-bw-destination.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="abd90-106">Microsoft Connector 1.1 for SAP BW に関するドキュメントでは、SAP Netweaver BW 環境について理解していることを前提としています。</span><span class="sxs-lookup"><span data-stu-id="abd90-106">The documentation for the Microsoft Connector 1.1 for SAP BW assumes familiarity with the SAP Netweaver BW environment.</span></span> <span data-ttu-id="abd90-107">SAP Netweaver BW の詳細または SAP Netweaver BW オブジェクトやプロセスを構成する方法については、SAP のマニュアルを参照してください。</span><span class="sxs-lookup"><span data-stu-id="abd90-107">For more information about SAP Netweaver BW, or for information about how to configure SAP Netweaver BW objects and processes, see your SAP documentation.</span></span>  
  
 <span data-ttu-id="abd90-108">**[新しいインフォオブジェクトの作成] ダイアログ ボックスを開くには**</span><span class="sxs-lookup"><span data-stu-id="abd90-108">**To open the Create New InfoObject dialog box**</span></span>  
  
1.  <span data-ttu-id="abd90-109">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]で、SAP BW 変換先が含まれている [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージを開きます。</span><span class="sxs-lookup"><span data-stu-id="abd90-109">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package that contains the SAP BW destination.</span></span>  
  
2.  <span data-ttu-id="abd90-110">**[データ フロー]** タブで、SAP BW 変換先をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="abd90-110">On the **Data Flow** tab, double-click the SAP BW destination.</span></span>  
  
3.  <span data-ttu-id="abd90-111">**[SAP BW 変換先エディター]** で、 **[接続マネージャー]** をクリックして **[接続マネージャー]** ページを開きます。</span><span class="sxs-lookup"><span data-stu-id="abd90-111">In the **SAP BW Destination Editor**, click **Connection Manager** to open the **Connection Manager** page of the editor.</span></span>  
  
4.  <span data-ttu-id="abd90-112">**[接続マネージャー]** ページの **[SAP BW オブジェクトの作成]** で、以下のいずれかの手順に従ってインフォオブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="abd90-112">On the **Connection Manager** page, in the **Create SAP BW Objects** group box, do one of the following steps to create an InfoObject:</span></span>  
  
    1.  <span data-ttu-id="abd90-113">インフォオブジェクトを直接作成するには、 **[インフォオブジェクト]** を選択し、 **[作成]** をクリックして、 **[新しいインフォオブジェクトの作成]** ダイアログ ボックスを開きます。</span><span class="sxs-lookup"><span data-stu-id="abd90-113">To create an InfoObject directly, select **InfoObject**, and then click **Create** to open the **Create New InfoObject** dialog box.</span></span>  
  
    2.  <span data-ttu-id="abd90-114">インフォキューブの作成中にインフォオブジェクトを作成するには、 **[インフォキューブ]** を選択して、 **[作成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="abd90-114">To create an InfoObject while creating an InfoCube, select **InfoCube**, and then click **Create**.</span></span> <span data-ttu-id="abd90-115">**[トランザクション データのインフォキューブの作成]** ダイアログ ボックスで、一覧の行の 1 つから **[IObject]** 列の **[作成]** を選択して、 **[新しいインフォオブジェクトの作成]** ダイアログ ボックスを開きます。</span><span class="sxs-lookup"><span data-stu-id="abd90-115">In the **Create InfoCube for Transaction Data** dialog box, in the **IObject** column for one of the rows in the list, select **Create** to open the **Create New InfoObject** dialog box.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="abd90-116">テーブルの各行は、パッケージのデータ フローの列を表します。</span><span class="sxs-lookup"><span data-stu-id="abd90-116">Each row in the table represents a column in the data flow of the package.</span></span>  
  
    3.  <span data-ttu-id="abd90-117">トランザクション データ用のインフォソースの作成中にインフォオブジェクトを作成するには、 **[インフォソース]** を選択して、 **[作成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="abd90-117">To create an InfoObject while creating an InfoSouce for transactional data, select **InfoSource**, and then click **Create**.</span></span> <span data-ttu-id="abd90-118">**[インフォソースの作成]** ダイアログ ボックスで、 **[トランザクション データ]** を選択して **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="abd90-118">In the **Create InfoSource** dialog box, select **Transaction Data**, and then click **OK**.</span></span> <span data-ttu-id="abd90-119">**[トランザクション データのインフォソースの作成]** ダイアログ ボックスで、一覧の行の 1 つから **[IObject]** 列の **[作成]** を選択して、 **[新しいインフォオブジェクトの作成]** ダイアログ ボックスを開きます。</span><span class="sxs-lookup"><span data-stu-id="abd90-119">In the **Create InfoSource for Transaction Data** dialog box, in the **IObject** column for one of the rows in the list, select **Create** to open the **Create New InfoObject** dialog box.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="abd90-120">テーブルの各行は、パッケージのデータ フローの列を表します。</span><span class="sxs-lookup"><span data-stu-id="abd90-120">Each row in the table represents a column in the data flow of the package.</span></span>  
  
    4.  <span data-ttu-id="abd90-121">マスター データ用のインフォソースの作成中にインフォオブジェクトを作成するには、 **[インフォソース]** を選択して、 **[作成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="abd90-121">To create an InfoObject while creating an InfoSource for master data, select **InfoSource**, and then click **Create**.</span></span> <span data-ttu-id="abd90-122">**[インフォソースの作成]** ダイアログ ボックスで、 **[マスター データ]** を選択して **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="abd90-122">In the **Create InfoSource** dialog box, select **Master Data**, and then click **OK**.</span></span> <span data-ttu-id="abd90-123">**[マスター データのインフォソースの作成]** ダイアログ ボックスで、 **[新規作成]** をクリックして、 **[新しいインフォオブジェクトの作成]** ダイアログ ボックスを開きます。</span><span class="sxs-lookup"><span data-stu-id="abd90-123">In the **Create InfoSource for Master Data** dialog box, click **New** to open the **Create New InfoObject** dialog box.</span></span>  
  
 <span data-ttu-id="abd90-124">**[新しいインフォオブジェクトの作成]** ダイアログ ボックスは、 **[新しいインフォオブジェクトの作成]** ダイアログ ボックスの **[属性]** セクションで **[新規作成]** をクリックして開くこともできます。</span><span class="sxs-lookup"><span data-stu-id="abd90-124">You can also open the **Create New InfoObject** dialog box by clicking **New** in the **Attributes** section of the **Create New InfoObject** dialog box.</span></span>  
  
## <a name="general-options"></a><span data-ttu-id="abd90-125">[全般] のオプション</span><span class="sxs-lookup"><span data-stu-id="abd90-125">General Options</span></span>  
 <span data-ttu-id="abd90-126">**特性**</span><span class="sxs-lookup"><span data-stu-id="abd90-126">**Characteristic**</span></span>  
 <span data-ttu-id="abd90-127">ディメンション データを表すインフォオブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="abd90-127">Create an InfoObject that represents dimension data.</span></span>  
  
 <span data-ttu-id="abd90-128">**主要データ**</span><span class="sxs-lookup"><span data-stu-id="abd90-128">**Key figure**</span></span>  
 <span data-ttu-id="abd90-129">ファクト データを表すインフォオブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="abd90-129">Create an InfoObject that represents fact data.</span></span>  
  
 <span data-ttu-id="abd90-130">**インフォオブジェクトの名前**</span><span class="sxs-lookup"><span data-stu-id="abd90-130">**InfoObject name**</span></span>  
 <span data-ttu-id="abd90-131">インフォオブジェクトの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="abd90-131">Enter a name for the InfoObject.</span></span>  
  
 <span data-ttu-id="abd90-132">**簡単な説明**</span><span class="sxs-lookup"><span data-stu-id="abd90-132">**Short description**</span></span>  
 <span data-ttu-id="abd90-133">インフォオブジェクトの短い説明を入力します。</span><span class="sxs-lookup"><span data-stu-id="abd90-133">Enter a short description for the InfoObject.</span></span>  
  
 <span data-ttu-id="abd90-134">**長い説明**</span><span class="sxs-lookup"><span data-stu-id="abd90-134">**Long description**</span></span>  
 <span data-ttu-id="abd90-135">インフォオブジェクトの長い説明を入力します。</span><span class="sxs-lookup"><span data-stu-id="abd90-135">Enter a long description for the InfoObject.</span></span>  
  
 <span data-ttu-id="abd90-136">**マスター データがある**</span><span class="sxs-lookup"><span data-stu-id="abd90-136">**Has master data**</span></span>  
 <span data-ttu-id="abd90-137">インフォオブジェクトが属性、テキスト、階層の形式でマスター データを含むことを示します。</span><span class="sxs-lookup"><span data-stu-id="abd90-137">Indicate that the InfoObject contains master data in the form of attributes, texts, or hierarchies.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="abd90-138">インフォオブジェクトが次元データを表し、 **[特性]** オプションを選択している場合、このオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="abd90-138">Select this option if the InfoObject represents dimensional data and you have selected the **Characteristic** option.</span></span>  
  
 <span data-ttu-id="abd90-139">**小文字を許可する**</span><span class="sxs-lookup"><span data-stu-id="abd90-139">**Allow lower-case characters**</span></span>  
 <span data-ttu-id="abd90-140">インフォオブジェクトのデータの小文字を許可します。</span><span class="sxs-lookup"><span data-stu-id="abd90-140">Allow lower-case characters in the InfoObject data.</span></span>  
  
 <span data-ttu-id="abd90-141">**保存と有効化**</span><span class="sxs-lookup"><span data-stu-id="abd90-141">**Save & Activate**</span></span>  
 <span data-ttu-id="abd90-142">新しいインフォオブジェクトを保存してアクティブ化します。</span><span class="sxs-lookup"><span data-stu-id="abd90-142">Save and active the new InfoObject.</span></span>  
  
## <a name="data-type-options"></a><span data-ttu-id="abd90-143">[データ型] オプション</span><span class="sxs-lookup"><span data-stu-id="abd90-143">Data Type Options</span></span>  
 <span data-ttu-id="abd90-144">**CHAR - 文字列**</span><span class="sxs-lookup"><span data-stu-id="abd90-144">**CHAR - Character String**</span></span>  
 <span data-ttu-id="abd90-145">インフォオブジェクト オブジェクトに文字データが含まれていることを示します。</span><span class="sxs-lookup"><span data-stu-id="abd90-145">Indicates that the InfoObject contains character data.</span></span>  
  
 <span data-ttu-id="abd90-146">**NUMC - 数値文字列**</span><span class="sxs-lookup"><span data-stu-id="abd90-146">**NUMC - Numeric String**</span></span>  
 <span data-ttu-id="abd90-147">インフォオブジェクト オブジェクトに数値データが含まれていることを示します。</span><span class="sxs-lookup"><span data-stu-id="abd90-147">Indicates that the InfoObject contains numeric data.</span></span>  
  
 <span data-ttu-id="abd90-148">**DATS - 日付 (YYYYMMDD)**</span><span class="sxs-lookup"><span data-stu-id="abd90-148">**DATS - Date (YYYYMMDD)**</span></span>  
 <span data-ttu-id="abd90-149">インフォオブジェクト オブジェクトに日付データが含まれていることを示します。</span><span class="sxs-lookup"><span data-stu-id="abd90-149">Indicates that the InfoObject contains date data.</span></span>  
  
 <span data-ttu-id="abd90-150">**TIMS - 時刻 (HHMMSS)**</span><span class="sxs-lookup"><span data-stu-id="abd90-150">**TIMS - Time (HHMMSS)**</span></span>  
 <span data-ttu-id="abd90-151">インフォオブジェクト オブジェクトに時刻データが含まれていることを示します。</span><span class="sxs-lookup"><span data-stu-id="abd90-151">Indicates that the InfoObject contains time data.</span></span>  
  
 <span data-ttu-id="abd90-152">**[データ型]**</span><span class="sxs-lookup"><span data-stu-id="abd90-152">**Length**</span></span>  
 <span data-ttu-id="abd90-153">データ型の長さを入力します。</span><span class="sxs-lookup"><span data-stu-id="abd90-153">Enter the length of the data.</span></span>  
  
## <a name="text-options"></a><span data-ttu-id="abd90-154">[テキスト] のオプション</span><span class="sxs-lookup"><span data-stu-id="abd90-154">Text Options</span></span>  
 <span data-ttu-id="abd90-155">**テキスト付き**</span><span class="sxs-lookup"><span data-stu-id="abd90-155">**With Texts**</span></span>  
 <span data-ttu-id="abd90-156">インフォオブジェクト オブジェクトにテキストが含まれていることを示します。</span><span class="sxs-lookup"><span data-stu-id="abd90-156">Indicate that the InfoObject contains texts.</span></span>  
  
 <span data-ttu-id="abd90-157">**短いテキスト**</span><span class="sxs-lookup"><span data-stu-id="abd90-157">**Short Text**</span></span>  
 <span data-ttu-id="abd90-158">インフォオブジェクト オブジェクトに短いテキストが含まれていることを示します。</span><span class="sxs-lookup"><span data-stu-id="abd90-158">Indicates that the InfoObject contains short texts.</span></span>  
  
 <span data-ttu-id="abd90-159">**中程度のテキスト**</span><span class="sxs-lookup"><span data-stu-id="abd90-159">**Medium Text**</span></span>  
 <span data-ttu-id="abd90-160">インフォオブジェクト オブジェクトに中程度のテキストが含まれていることを示します。</span><span class="sxs-lookup"><span data-stu-id="abd90-160">Indicates that the InfoObject contains medium texts.</span></span>  
  
 <span data-ttu-id="abd90-161">**長いテキスト**</span><span class="sxs-lookup"><span data-stu-id="abd90-161">**Long Text**</span></span>  
 <span data-ttu-id="abd90-162">インフォオブジェクト オブジェクトに長いテキストが含まれていることを示します。</span><span class="sxs-lookup"><span data-stu-id="abd90-162">Indicates that the InfoObject contains long texts.</span></span>  
  
 <span data-ttu-id="abd90-163">**テキストの言語に依存**</span><span class="sxs-lookup"><span data-stu-id="abd90-163">**Text Language-Dependent**</span></span>  
 <span data-ttu-id="abd90-164">テキストが言語に依存することを示します。</span><span class="sxs-lookup"><span data-stu-id="abd90-164">Indicates that the texts are language-dependent.</span></span>  
  
 <span data-ttu-id="abd90-165">**テキストの時間に依存**</span><span class="sxs-lookup"><span data-stu-id="abd90-165">**Text Time-Dependent**</span></span>  
 <span data-ttu-id="abd90-166">テキストが時間に依存することを示します。</span><span class="sxs-lookup"><span data-stu-id="abd90-166">Indicates that the texts are time-dependent.</span></span>  
  
## <a name="attributes-section"></a><span data-ttu-id="abd90-167">[属性] セクション</span><span class="sxs-lookup"><span data-stu-id="abd90-167">Attributes Section</span></span>  
 <span data-ttu-id="abd90-168">**[属性]** セクションはインフォオブジェクトの属性の一覧、および一覧に属性を追加および一覧から削除を行えるオプションで構成されています。</span><span class="sxs-lookup"><span data-stu-id="abd90-168">The **Attributes** section consists of a list of attributes for the InfoObject, and the options that let you add and remove attributes from the list.</span></span>  
  
### <a name="attributes-list"></a><span data-ttu-id="abd90-169">[属性] の一覧</span><span class="sxs-lookup"><span data-stu-id="abd90-169">Attributes List</span></span>  
 <span data-ttu-id="abd90-170">**[属性]** ボックスの一覧には、作成するインフォオブジェクトの属性が表示されます。</span><span class="sxs-lookup"><span data-stu-id="abd90-170">The **Attributes** list displays the attributes of the InfoObject that you are creating.</span></span> <span data-ttu-id="abd90-171">**[属性]** の一覧には次の列見出しがあります:</span><span class="sxs-lookup"><span data-stu-id="abd90-171">The **Attributes** list has the following column headings:</span></span>  
  
 <span data-ttu-id="abd90-172">**インフォオブジェクト**</span><span class="sxs-lookup"><span data-stu-id="abd90-172">**InfoObject**</span></span>  
 <span data-ttu-id="abd90-173">インフォオブジェクトの名前を表示します。</span><span class="sxs-lookup"><span data-stu-id="abd90-173">View the name of the InfoObject.</span></span>  
  
 <span data-ttu-id="abd90-174">**説明**</span><span class="sxs-lookup"><span data-stu-id="abd90-174">**Description**</span></span>  
 <span data-ttu-id="abd90-175">インフォオブジェクトの説明を表示します。</span><span class="sxs-lookup"><span data-stu-id="abd90-175">View the description of the InfoObject.</span></span>  
  
 <span data-ttu-id="abd90-176">**インフォオブジェクトの種類**</span><span class="sxs-lookup"><span data-stu-id="abd90-176">**InfoObject Type**</span></span>  
 <span data-ttu-id="abd90-177">インフォオブジェクトの種類を表示します。</span><span class="sxs-lookup"><span data-stu-id="abd90-177">View the type of the InfoObject.</span></span> <span data-ttu-id="abd90-178">次の表に、種類として使用できる値の一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="abd90-178">The following table lists the possible values for the type.</span></span>  
  
|<span data-ttu-id="abd90-179">値</span><span class="sxs-lookup"><span data-stu-id="abd90-179">Value</span></span>|<span data-ttu-id="abd90-180">説明</span><span class="sxs-lookup"><span data-stu-id="abd90-180">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="abd90-181">CHA</span><span class="sxs-lookup"><span data-stu-id="abd90-181">CHA</span></span>|<span data-ttu-id="abd90-182">特性</span><span class="sxs-lookup"><span data-stu-id="abd90-182">Characteristics</span></span>|  
|<span data-ttu-id="abd90-183">KYF</span><span class="sxs-lookup"><span data-stu-id="abd90-183">KYF</span></span>|<span data-ttu-id="abd90-184">主要データ</span><span class="sxs-lookup"><span data-stu-id="abd90-184">Key figures</span></span>|  
|<span data-ttu-id="abd90-185">UNI</span><span class="sxs-lookup"><span data-stu-id="abd90-185">UNI</span></span>|<span data-ttu-id="abd90-186">Units</span><span class="sxs-lookup"><span data-stu-id="abd90-186">Units</span></span>|  
|<span data-ttu-id="abd90-187">TIM</span><span class="sxs-lookup"><span data-stu-id="abd90-187">TIM</span></span>|<span data-ttu-id="abd90-188">時間の特性</span><span class="sxs-lookup"><span data-stu-id="abd90-188">Time characteristics</span></span>|  
  
### <a name="attributes-options"></a><span data-ttu-id="abd90-189">[属性] のオプション</span><span class="sxs-lookup"><span data-stu-id="abd90-189">Attributes Options</span></span>  
 <span data-ttu-id="abd90-190">作成するインフォオブジェクトの属性を追加または削除するには、次のオプションを使用します。</span><span class="sxs-lookup"><span data-stu-id="abd90-190">Use the following options to add and remove attributes for the InfoObject that you are creating:</span></span>  
  
 <span data-ttu-id="abd90-191">**追加**</span><span class="sxs-lookup"><span data-stu-id="abd90-191">**Add**</span></span>  
 <span data-ttu-id="abd90-192">属性として既存のインフォオブジェクトを追加します。</span><span class="sxs-lookup"><span data-stu-id="abd90-192">Add an existing InfoObject as an attribute.</span></span>  
  
 <span data-ttu-id="abd90-193">既存のインフォオブジェクトを追加するには、[追加] をクリックし、 **[インフォオブジェクトの参照]** ダイアログ ボックスを使用してインフォオブジェクトを検索します。</span><span class="sxs-lookup"><span data-stu-id="abd90-193">To add an existing InfoObject, click Add, and then use the **Look Up InfoObject** dialog box to find the InfoObject.</span></span> <span data-ttu-id="abd90-194">このダイアログ ボックスの詳細については、「 [インフォオブジェクトの参照](look-up-infoobject.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="abd90-194">For more information about this dialog box, see [Look Up InfoObject](look-up-infoobject.md).</span></span>  
  
 <span data-ttu-id="abd90-195">**[新規作成]**</span><span class="sxs-lookup"><span data-stu-id="abd90-195">**New**</span></span>  
 <span data-ttu-id="abd90-196">属性として新しいインフォオブジェクトを追加します。</span><span class="sxs-lookup"><span data-stu-id="abd90-196">Add a new InfoObject as an attribute.</span></span>  
  
 <span data-ttu-id="abd90-197">新しいインフォオブジェクトを作成して追加するには、[新規作成] をクリックし、 **[新しいインフォオブジェクトの作成]** ダイアログ ボックスの新しいインスタンスを使用して、新しいインフォオブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="abd90-197">To create and add a new InfoObject, click New, and then use a new instance of the **Create New InfoObject** dialog box to create the new InfoObject.</span></span>  
  
 <span data-ttu-id="abd90-198">**Remove**</span><span class="sxs-lookup"><span data-stu-id="abd90-198">**Remove**</span></span>  
 <span data-ttu-id="abd90-199">選択したインフォオブジェクトを **[属性]** の一覧から削除します。</span><span class="sxs-lookup"><span data-stu-id="abd90-199">Remove the selected InfoObject from the **Attributes** list.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="abd90-200">参照</span><span class="sxs-lookup"><span data-stu-id="abd90-200">See Also</span></span>  
 <span data-ttu-id="abd90-201">[[トランザクション データのインフォキューブの作成]](create-infocube-for-transaction-data.md) </span><span class="sxs-lookup"><span data-stu-id="abd90-201">[Create InfoCube for Transaction Data](create-infocube-for-transaction-data.md) </span></span>  
 <span data-ttu-id="abd90-202">[[インフォソースの作成]](create-infosource.md) </span><span class="sxs-lookup"><span data-stu-id="abd90-202">[Create InfoSource](create-infosource.md) </span></span>  
 <span data-ttu-id="abd90-203">[トランザクション データのインフォソースの作成](create-infosource-for-transaction-data.md) </span><span class="sxs-lookup"><span data-stu-id="abd90-203">[Create InfoSource for Transaction Data](create-infosource-for-transaction-data.md) </span></span>  
 <span data-ttu-id="abd90-204">[マスター データのインフォソースの作成](create-infosource-for-master-data.md) </span><span class="sxs-lookup"><span data-stu-id="abd90-204">[Create InfoSource for Master Data](create-infosource-for-master-data.md) </span></span>  
 [<span data-ttu-id="abd90-205">Microsoft Connector 1.1 for SAP BW の F1 ヘルプ</span><span class="sxs-lookup"><span data-stu-id="abd90-205">Microsoft Connector 1.1 for SAP BW F1 Help</span></span>](../microsoft-connector-for-sap-bw-f1-help.md)  
  
  
