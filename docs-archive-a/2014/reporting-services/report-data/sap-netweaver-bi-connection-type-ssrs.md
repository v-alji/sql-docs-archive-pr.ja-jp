---
title: SAP NetWeaver BI の接続の種類 (SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: f985856b-31d5-4e56-844b-8a8ee38da67e
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 42806e370e20257f5de9e49d4f59dd3bb7793f20
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742853"
---
# <a name="sap-netweaver-bi-connection-type-ssrs"></a><span data-ttu-id="445f8-102">SAP NetWeaver BI の接続の種類 (SSRS)</span><span class="sxs-lookup"><span data-stu-id="445f8-102">SAP NetWeaver BI Connection Type (SSRS)</span></span>
  <span data-ttu-id="445f8-103">SAP NetWeaver® Business Intelligence の外部データ ソースのデータをレポートに含めるには、種類が [!INCLUDE[SAP_DPE_BW_1](../../includes/sap-dpe-bw-1-md.md)]のレポート データ ソースに基づいたデータセットが必要です。</span><span class="sxs-lookup"><span data-stu-id="445f8-103">To include data from a SAP NetWeaver® Business Intelligence external data source in your report, you must have a dataset that is based on a report data source of type [!INCLUDE[SAP_DPE_BW_1](../../includes/sap-dpe-bw-1-md.md)].</span></span> <span data-ttu-id="445f8-104">このビルトイン データ ソースの種類は、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework Data Provider 1.0 for [!INCLUDE[SAP_DPE_BW_1](../../includes/sap-dpe-bw-1-md.md)]のデータ拡張機能に基づいています。</span><span class="sxs-lookup"><span data-stu-id="445f8-104">This built-in data source type is based on the data extension for the [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework Data Provider 1.0 for [!INCLUDE[SAP_DPE_BW_1](../../includes/sap-dpe-bw-1-md.md)].</span></span>  
  
 <span data-ttu-id="445f8-105">このデータ拡張機能を使用すると、 [!INCLUDE[SAP_DPE_BW_1](../../includes/sap-dpe-bw-1-md.md)] の外部データ ソースで定義された InfoCube、MultiProvider (仮想 InfoCube)、および Web 対応クエリから多次元データを取得できます。</span><span class="sxs-lookup"><span data-stu-id="445f8-105">This data extension enables you to retrieve multidimensional data from InfoCubes, MultiProviders (virtual InfoCubes), and Web-enabled queries that are defined on a [!INCLUDE[SAP_DPE_BW_1](../../includes/sap-dpe-bw-1-md.md)] external data source.</span></span>  
  
 <span data-ttu-id="445f8-106">このトピックの情報を使用して、データ ソースを構築してください。</span><span class="sxs-lookup"><span data-stu-id="445f8-106">Use the information in this topic to build a data source.</span></span> <span data-ttu-id="445f8-107">詳細な手順については、「[データ接続またはデータソース &#40;レポートビルダーと SSRS&#41;の追加と検証](add-and-verify-a-data-connection-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="445f8-107">For step-by-step instructions, see [Add and Verify a Data Connection or Data Source &#40;Report Builder and SSRS&#41;](add-and-verify-a-data-connection-report-builder-and-ssrs.md).</span></span>  
  
##  <a name="supported-versions"></a><a name="support"></a><span data-ttu-id="445f8-108">サポートされるバージョン</span><span class="sxs-lookup"><span data-stu-id="445f8-108">Supported Versions</span></span>  
 <span data-ttu-id="445f8-109">SAP BW 3.5 および 7.0 に対して、データ プロバイダーが開発され、テストが実施されています。</span><span class="sxs-lookup"><span data-stu-id="445f8-109">The data provider has been developed for and tested against SAP BW 3.5 and 7.0.</span></span>  
  
-   <span data-ttu-id="445f8-110">SAP BW 3.5 および 7.0 の サポート パッケージ 20</span><span class="sxs-lookup"><span data-stu-id="445f8-110">Support Package 20 for SAP BW 3.5 and 7.0</span></span>  
  
 <span data-ttu-id="445f8-111">次のシステムに対して、Windows 統合認証用のプロバイダーが開発され、テストが実施されています。</span><span class="sxs-lookup"><span data-stu-id="445f8-111">For Windows Integrated Authentication the provider was developed for and tested against the following systems.</span></span>  
  
-   <span data-ttu-id="445f8-112">SAP Portals 6.40 サポート パッケージ 20</span><span class="sxs-lookup"><span data-stu-id="445f8-112">SAP Portals 6.40 Support Package 20</span></span>  
  
-   <span data-ttu-id="445f8-113">SAP ポータル7.0 サポートパッケージ11</span><span class="sxs-lookup"><span data-stu-id="445f8-113">SAP Portals 7.0 Support Package 11</span></span>  
  
-   <span data-ttu-id="445f8-114">SAP Duet 1.0</span><span class="sxs-lookup"><span data-stu-id="445f8-114">SAP Duet 1.0</span></span>  
  
##  <a name="connection-string"></a><a name="Connection"></a><span data-ttu-id="445f8-115">接続文字列</span><span class="sxs-lookup"><span data-stu-id="445f8-115">Connection String</span></span>  
 <span data-ttu-id="445f8-116">データ ソースに接続するときに使用する接続情報および資格情報については、データベース管理者に問い合わせてください。</span><span class="sxs-lookup"><span data-stu-id="445f8-116">Contact the database administrator for connection information and for the credentials to use to connect to the data source.</span></span> <span data-ttu-id="445f8-117">次の接続文字列では、8000 番ポートを使用してサーバー上の [!INCLUDE[SAP_DPE_BW_1](../../includes/sap-dpe-bw-1-md.md)] データ ソースを指定し、SOAP を使用してインターネット経由の XML for Analysis Services (XMLA) を指定しています。</span><span class="sxs-lookup"><span data-stu-id="445f8-117">The following connection string example specifies an [!INCLUDE[SAP_DPE_BW_1](../../includes/sap-dpe-bw-1-md.md)] data source on a server using port 8000 and XML for Analysis Services (XMLA) over the Internet using SOAP:</span></span>  
  
```  
DataSource=http://mySAPNetWeaverBIServer:8000/sap/bw/xml/soap/xmla  
```  
  
 <span data-ttu-id="445f8-118">接続文字列の例について詳しくは、「 [レポート ビルダーでのデータ接続、データ ソース、および接続文字列](../data-connections-data-sources-and-connection-strings-in-report-builder.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="445f8-118">For more connection string examples, see [Data Connections, Data Sources, and Connection Strings in Report Builder](../data-connections-data-sources-and-connection-strings-in-report-builder.md).</span></span>  
  
  
  
##  <a name="credentials"></a><a name="Credentials"></a><span data-ttu-id="445f8-119">認証</span><span class="sxs-lookup"><span data-stu-id="445f8-119">Credentials</span></span>  
 <span data-ttu-id="445f8-120">クエリの実行、ローカルでのレポートのプレビュー、およびレポート サーバーからのレポートのプレビューには、資格情報が必要です。</span><span class="sxs-lookup"><span data-stu-id="445f8-120">Credentials are required to run queries, to preview the report locally, and to preview the report from the report server.</span></span>  
  
 <span data-ttu-id="445f8-121">レポートをパブリッシュした後、レポートをレポート サーバーで実行するときに、データを取得するための権限が有効な状態になるように、データ ソースの資格情報を変更する必要が生じる場合があります。</span><span class="sxs-lookup"><span data-stu-id="445f8-121">After you publish your report, you may need to change the credentials for the data source so that when the report runs on the report server, the permissions to retrieve the data are valid.</span></span>  
  
 <span data-ttu-id="445f8-122">詳細については、「 [Reporting Services のデータ接続、データソース、および接続文字列](../data-connections-data-sources-and-connection-strings-in-reporting-services.md)」または「[レポートビルダーで資格情報を指定する](../specify-credentials-in-report-builder.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="445f8-122">For more information, see [Data Connections, Data Sources, and Connection Strings in Reporting Services](../data-connections-data-sources-and-connection-strings-in-reporting-services.md) or [Specify Credentials in Report Builder](../specify-credentials-in-report-builder.md).</span></span>  
  
  
  
##  <a name="queries"></a><a name="Query"></a><span data-ttu-id="445f8-123">問い合わせ</span><span class="sxs-lookup"><span data-stu-id="445f8-123">Queries</span></span>  
 <span data-ttu-id="445f8-124">グラフィカル クエリ デザイナーのデザイン モードまたはクエリ モードを使用すると、データ ソース上の基になるデータ構造を参照しながら、多次元式 (MDX) クエリを作成できます。</span><span class="sxs-lookup"><span data-stu-id="445f8-124">You can use the graphical query designer in Design or Query mode to build a Multidimensional Expression (MDX) query by browsing the underlying data structures on the data source.</span></span> <span data-ttu-id="445f8-125">デザイン時には、クエリ デザイナーから対話的にクエリを実行して結果を確認することができます。</span><span class="sxs-lookup"><span data-stu-id="445f8-125">At design time, you can interactively run a query from the query designer to see the results.</span></span> <span data-ttu-id="445f8-126">作成したクエリによって、データセットのフィールドが定義されます。</span><span class="sxs-lookup"><span data-stu-id="445f8-126">The query you build defines fields in the dataset.</span></span> <span data-ttu-id="445f8-127">実行時には、データ ソースから実際のデータが返されます。</span><span class="sxs-lookup"><span data-stu-id="445f8-127">At run time, the actual data is returned from the data source.</span></span> <span data-ttu-id="445f8-128">グラフィカル クエリ デザイナーでは、次の操作を実行できます。</span><span class="sxs-lookup"><span data-stu-id="445f8-128">Use the graphical query designer to perform the following actions:</span></span>  
  
-   <span data-ttu-id="445f8-129">デザイン モードでは、ディメンション、メンバー、メンバーのプロパティ、主要データなどを、データ ソースからデータ ペインにドラッグして、多次元式 (MDX) クエリを作成できます。</span><span class="sxs-lookup"><span data-stu-id="445f8-129">In Design mode, drag dimensions, members, member properties, and key figures from the data source onto a Data pane to build a Multidimensional Expression (MDX) query.</span></span> <span data-ttu-id="445f8-130">計算されるメンバー ペインから、計算されるメンバーをデータ ペインにドラッグして、追加のデータセット フィールドを定義できます。</span><span class="sxs-lookup"><span data-stu-id="445f8-130">Drag calculated members from the Calculated Members pane to the Data pane to define additional dataset fields.</span></span>  
  
-   <span data-ttu-id="445f8-131">クエリ モードでは、ディメンション、メンバー、メンバーのプロパティ、主要データなどをクエリ ペインにドラッグするか、MDX テキストを直接クエリ ペインに入力できます。</span><span class="sxs-lookup"><span data-stu-id="445f8-131">In Query mode, drag dimensions, members, member properties, and key figures onto the Query pane or type MDX text directly into the Query pane.</span></span> <span data-ttu-id="445f8-132">計算されるメンバー ペインから、計算されるメンバーをデータ ペインにドラッグして、追加のデータセット フィールドを定義できます。</span><span class="sxs-lookup"><span data-stu-id="445f8-132">Drag calculated members from the Calculated Members pane to the Data pane to define additional dataset fields.</span></span>  
  
 <span data-ttu-id="445f8-133">クエリを作成すると、クエリ デザイナーは MDX クエリに既定のプロパティを自動的に追加します。</span><span class="sxs-lookup"><span data-stu-id="445f8-133">As you build queries, the query designer automatically adds default properties to the MDX query.</span></span> <span data-ttu-id="445f8-134">既定のプロパティ以外のプロパティを含めるには、MDX クエリを手動で変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="445f8-134">To include properties other than default properties, you must manually modify the MDX query.</span></span>  
  
 <span data-ttu-id="445f8-135">関連付けられているクエリ デザイナーについて詳しくは、「[SAP NetWeaver BI Query Designer のユーザー インターフェイス&#40;レポート ビルダー&#41;](../sap-netweaver-bi-query-designer-user-interface-report-builder.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="445f8-135">For more information about working with this query designer, see [SAP NetWeaver BI Query Designer User Interface &#40;Report Builder&#41;](../sap-netweaver-bi-query-designer-user-interface-report-builder.md).</span></span>  
  
  
  
##  <a name="extended-field-properties"></a><a name="Extended"></a> <span data-ttu-id="445f8-136">拡張フィールド プロパティ</span><span class="sxs-lookup"><span data-stu-id="445f8-136">Extended Field Properties</span></span>  
 <span data-ttu-id="445f8-137">[!INCLUDE[SAP_DPE_BW_1](../../includes/sap-dpe-bw-1-md.md)] データ ソースは、拡張フィールド プロパティをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="445f8-137">The [!INCLUDE[SAP_DPE_BW_1](../../includes/sap-dpe-bw-1-md.md)] data source supports extended field properties.</span></span> <span data-ttu-id="445f8-138">拡張フィールド プロパティは、`Value` と `IsMissing` に追加する形で、データ処理拡張機能によってデータセットのフィールドに定義されるプロパティです。</span><span class="sxs-lookup"><span data-stu-id="445f8-138">Extended field properties are properties in addition to `Value` and `IsMissing` that are defined for a dataset field by the data processing extension.</span></span> <span data-ttu-id="445f8-139">拡張プロパティには、定義済みプロパティとカスタム プロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="445f8-139">Extended properties include predefined properties and custom properties.</span></span> <span data-ttu-id="445f8-140">定義済みのプロパティは、複数のデータ ソースに共通のプロパティです。</span><span class="sxs-lookup"><span data-stu-id="445f8-140">Predefined properties are properties common to multiple data sources.</span></span> <span data-ttu-id="445f8-141">カスタム プロパティは、各データ ソースの固有のプロパティです。</span><span class="sxs-lookup"><span data-stu-id="445f8-141">Custom properties are unique to each data source.</span></span>  
  
### <a name="working-with-field-properties"></a><span data-ttu-id="445f8-142">フィールド プロパティの操作</span><span class="sxs-lookup"><span data-stu-id="445f8-142">Working with Field Properties</span></span>  
 <span data-ttu-id="445f8-143">拡張フィールド プロパティは、レポート レイアウトにドラッグすることのできるアイテムとして [レポート データ] ウィンドウには表示されません。</span><span class="sxs-lookup"><span data-stu-id="445f8-143">Extended field properties do not appear in the Report Data pane as items that you can drag onto your report layout.</span></span> <span data-ttu-id="445f8-144">その代わりに、このプロパティの親フィールドをレポートにドラッグすることによって、既定のプロパティである `Value` を必要なプロパティに変更することが可能です。</span><span class="sxs-lookup"><span data-stu-id="445f8-144">Instead, you drag the parent field of the property onto the report and then change the default property from `Value` to the property you want to use.</span></span> <span data-ttu-id="445f8-145">たとえば、MDX クエリ デザイナーで、メタデータ ペインからクエリ ペインにレベルをドロップすることによって **Calendar Year/Month Level 01** というフィールド名を作成した場合、カスタムの拡張プロパティ **Long Name** を式の中で参照するには、次の構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="445f8-145">For example, if the field name **Calendar Year/Month Level 01** is created in an MDX query designer by dropping a level from the Metadata pane onto the Query pane, you would refer to the custom extended property **Long Name** in an expression using the following syntax:</span></span>  
  
 `=Fields!Calendar_Year_Month_Level_01("Long Name")`  
  
 <span data-ttu-id="445f8-146">メタデータ ペインでフィールドにカーソルを合わせると、拡張フィールド プロパティの名前がツールヒントに表示されます。</span><span class="sxs-lookup"><span data-stu-id="445f8-146">The name for an extended field property appears in the ToolTip when you hover over a field in the Metadata pane.</span></span> <span data-ttu-id="445f8-147">基になっているデータの調査に使用できるクエリ デザイナーについて詳しくは、「 [SAP NetWeaver BI Query Designer のユーザー インターフェイス](sap-netweaver-bi-query-designer-user-interface.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="445f8-147">For more information about the query designers you can use to explore the underlying data, see [SAP NetWeaver BI Query Designer User Interface](sap-netweaver-bi-query-designer-user-interface.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="445f8-148">拡張フィールド プロパティに対応する値が存在するのは、レポートを実行して対応するデータセットのデータを取得する際に、データ ソースによって値が提供された場合のみです。</span><span class="sxs-lookup"><span data-stu-id="445f8-148">Values exist for extended field properties only if the data source provides these values when your report runs and retrieves the data for its datasets.</span></span> <span data-ttu-id="445f8-149">その場合、以下に示す構文を使用して、すべての式からこれらの `Field` プロパティ値を参照できます。</span><span class="sxs-lookup"><span data-stu-id="445f8-149">You can then refer to those `Field` property values from any expression using the syntax described below.</span></span> <span data-ttu-id="445f8-150">ただし、これらのフィールドはこのデータ プロバイダーに固有であり、レポート定義言語には含まれないため、これらの値に加えた変更はレポート定義には保存されません。</span><span class="sxs-lookup"><span data-stu-id="445f8-150">However, because these fields are specific to this data provider and not part of the report definition language, changes that you make to these values are not saved with the report definition.</span></span>  
  
 <span data-ttu-id="445f8-151">定義済みの拡張プロパティを式の中で参照するには、次のいずれかの構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="445f8-151">Use either of the following syntaxes to refer to predefined extended properties in an expression:</span></span>  
  
-   <span data-ttu-id="445f8-152">*Fields!FieldName.PropertyName*</span><span class="sxs-lookup"><span data-stu-id="445f8-152">*Fields!FieldName.PropertyName*</span></span>  
  
-   <span data-ttu-id="445f8-153">*フィールド!FieldName ("PropertyName")*</span><span class="sxs-lookup"><span data-stu-id="445f8-153">*Fields!FieldName("PropertyName")*</span></span>  
  
 <span data-ttu-id="445f8-154">カスタム拡張プロパティを式の中で参照するには、次の構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="445f8-154">Use the following syntax to refer to custom extended properties in an expression:</span></span>  
  
-   <span data-ttu-id="445f8-155">*フィールド!FieldName ("PropertyName")*</span><span class="sxs-lookup"><span data-stu-id="445f8-155">*Fields!FieldName("PropertyName")*</span></span>  
  
  
  
### <a name="predefined-field-properties"></a><span data-ttu-id="445f8-156">定義済みフィールド プロパティ</span><span class="sxs-lookup"><span data-stu-id="445f8-156">Predefined Field Properties</span></span>  
 <span data-ttu-id="445f8-157">次の表に、 [!INCLUDE[SAP_DPE_BW_1](../../includes/sap-dpe-bw-1-md.md)] データ ソースで使用できる定義済みフィールド プロパティの一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="445f8-157">The following table provides a list of predefined field properties that you can use for an [!INCLUDE[SAP_DPE_BW_1](../../includes/sap-dpe-bw-1-md.md)] data source.</span></span>  
  
|<span data-ttu-id="445f8-158">**Property**</span><span class="sxs-lookup"><span data-stu-id="445f8-158">**Property**</span></span>|<span data-ttu-id="445f8-159">**Type**</span><span class="sxs-lookup"><span data-stu-id="445f8-159">**Type**</span></span>|<span data-ttu-id="445f8-160">**説明/有効値**</span><span class="sxs-lookup"><span data-stu-id="445f8-160">**Description or expected value**</span></span>|  
|------------------|--------------|---------------------------------------|  
|`Value`|`Object`|<span data-ttu-id="445f8-161">フィールドのデータ値を指定します。</span><span class="sxs-lookup"><span data-stu-id="445f8-161">Specifies the data value of the field.</span></span>|  
|`IsMissing`|`Boolean`|<span data-ttu-id="445f8-162">フィールドが結果データセットに存在するかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="445f8-162">Indicates whether the field was found in the resulting data set.</span></span>|  
|`FormattedValue`|`String`|<span data-ttu-id="445f8-163">主要データの書式設定した値を返します。</span><span class="sxs-lookup"><span data-stu-id="445f8-163">Returns a formatted value for a key figure.</span></span>|  
|`BackgroundColor`|`String`|<span data-ttu-id="445f8-164">データベースで定義されたフィールドの背景色を返します。</span><span class="sxs-lookup"><span data-stu-id="445f8-164">Returns the background color defined in the database for the field.</span></span>|  
|`Color`|`String`|<span data-ttu-id="445f8-165">データベースで定義されたアイテムの前景色を返します。</span><span class="sxs-lookup"><span data-stu-id="445f8-165">Returns the foreground color defined in the database for the item.</span></span>|  
|`Key`|`Object`|<span data-ttu-id="445f8-166">レベルのキーを返します。</span><span class="sxs-lookup"><span data-stu-id="445f8-166">Returns the key for a level.</span></span>|  
|`LevelNumber`|`Integer`|<span data-ttu-id="445f8-167">親子階層の場合は、レベル番号またはディメンション番号を返します。</span><span class="sxs-lookup"><span data-stu-id="445f8-167">For parent-child hierarchies, returns the level or dimension number.</span></span>|  
|`ParentUniqueName`|`String`|<span data-ttu-id="445f8-168">親子階層の場合は、親レベルの完全修飾名を返します。</span><span class="sxs-lookup"><span data-stu-id="445f8-168">For parent-child hierarchies, returns a fully qualified name of the parent level.</span></span>|  
|`UniqueName`|`String`|<span data-ttu-id="445f8-169">レベルの完全修飾名を返します。</span><span class="sxs-lookup"><span data-stu-id="445f8-169">Returns the fully qualified name of a level.</span></span> <span data-ttu-id="445f8-170">たとえば、 `UniqueName` 従業員の値が *[0D_Company]. [10D_Department] を入力します。[11]*。</span><span class="sxs-lookup"><span data-stu-id="445f8-170">For example, the `UniqueName` value for an employee might be *[0D_Company].[10D_Department].[11]*.</span></span>|  
  
 <span data-ttu-id="445f8-171">フィールドおよびフィールド プロパティを式で使用する方法について詳しくは、「[式で使用される組み込みコレクション &#40;レポート ビルダーおよび SSRS&#41;](../report-design/built-in-collections-in-expressions-report-builder.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="445f8-171">For more information about using fields and field properties in an expression, see [Built-in Collections in Expressions &#40;Report Builder and SSRS&#41;](../report-design/built-in-collections-in-expressions-report-builder.md).</span></span>  
  
  
  
##  <a name="remarks"></a><a name="Remarks"></a> <span data-ttu-id="445f8-172">解説</span><span class="sxs-lookup"><span data-stu-id="445f8-172">Remarks</span></span>  
 <span data-ttu-id="445f8-173">このデータ プロバイダーでは使用できないレポート配信モードもあります。</span><span class="sxs-lookup"><span data-stu-id="445f8-173">Not all report delivery modes are supported by this data provider.</span></span> <span data-ttu-id="445f8-174">このデータ処理拡張機能では、データ ドリブン サブスクリプションを使ったレポートの配信はサポートされません。</span><span class="sxs-lookup"><span data-stu-id="445f8-174">Delivering reports through data-driven subscriptions is not supported for this data processing extension.</span></span> <span data-ttu-id="445f8-175">詳細については、「[サブスクライバー データに対して外部データ ソースを使用する (データ ドリブン サブスクリプション)](../subscriptions/use-an-external-data-source-for-subscriber-data-data-driven-subscription.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="445f8-175">For more information, see [Use an External Data Source for Subscriber Data &#40;Data-Driven Subscription&#41;](../subscriptions/use-an-external-data-source-for-subscriber-data-data-driven-subscription.md).</span></span>  
  
 <span data-ttu-id="445f8-176">詳しくは、「 [Using SQL Server 2008 Reporting Services with SAP NetWeaver Business Intelligence (SAP NetWeaver Business Intelligence で SQL Server 2008 Reporting Services を使用する)](https://go.microsoft.com/fwlink/?LinkId=167352)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="445f8-176">For more information, see [Using SQL Server 2008 Reporting Services with SAP NetWeaver Business Intelligence](https://go.microsoft.com/fwlink/?LinkId=167352).</span></span>  
  
  
  
##  <a name="how-to-topics"></a><a name="HowTo"></a><span data-ttu-id="445f8-177">操作方法に関するトピック</span><span class="sxs-lookup"><span data-stu-id="445f8-177">How-To Topics</span></span>  
 <span data-ttu-id="445f8-178">データ接続、データ ソース、およびデータセットを操作する手順について説明します。</span><span class="sxs-lookup"><span data-stu-id="445f8-178">This section contains step-by-step instructions for working with data connections, data sources, and datasets.</span></span>  
  
 [<span data-ttu-id="445f8-179">データ接続またはデータソース &#40;レポートビルダーと SSRS&#41;に追加して検証する</span><span class="sxs-lookup"><span data-stu-id="445f8-179">Add and Verify a Data Connection or Data Source &#40;Report Builder and SSRS&#41;</span></span>](add-and-verify-a-data-connection-report-builder-and-ssrs.md)  
  
 [<span data-ttu-id="445f8-180">共有データセットまたは埋め込みデータセットの作成 (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="445f8-180">Create a Shared Dataset or Embedded Dataset &#40;Report Builder and SSRS&#41;</span></span>](create-a-shared-dataset-or-embedded-dataset-report-builder-and-ssrs.md)  
  
 [<span data-ttu-id="445f8-181">データセットへのフィルターの追加 (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="445f8-181">Add a Filter to a Dataset &#40;Report Builder and SSRS&#41;</span></span>](add-a-filter-to-a-dataset-report-builder-and-ssrs.md)  
  
  
  
##  <a name="related-sections"></a><a name="Related"></a> <span data-ttu-id="445f8-182">関連セクション</span><span class="sxs-lookup"><span data-stu-id="445f8-182">Related Sections</span></span>  
 <span data-ttu-id="445f8-183">次に示すセクションでは、レポート データの概念が詳細に説明されているほか、データに関連するレポートのパーツを定義し、カスタマイズし、使用する方法が説明されています。</span><span class="sxs-lookup"><span data-stu-id="445f8-183">These sections of the documentation provide in-depth conceptual information about report data, as well as procedural information about how to define, customize, and use parts of a report that are related to data.</span></span>  
  
 [<span data-ttu-id="445f8-184">レポート &#40;レポートビルダーおよび SSRS&#41;にデータを追加する</span><span class="sxs-lookup"><span data-stu-id="445f8-184">Add Data to a Report &#40;Report Builder and SSRS&#41;</span></span>](report-datasets-ssrs.md)  
 <span data-ttu-id="445f8-185">レポートのデータへのアクセスの概要について説明します。</span><span class="sxs-lookup"><span data-stu-id="445f8-185">Provides an overview of accessing data for your report.</span></span>  
  
 [<span data-ttu-id="445f8-186">レポート ビルダーでのデータ接続、データ ソース、および接続文字列</span><span class="sxs-lookup"><span data-stu-id="445f8-186">Data Connections, Data Sources, and Connection Strings in Report Builder</span></span>](../data-connections-data-sources-and-connection-strings-in-report-builder.md)  
 <span data-ttu-id="445f8-187">データ接続とデータ ソースについて説明します。</span><span class="sxs-lookup"><span data-stu-id="445f8-187">Provides information about data connections and data sources.</span></span>  
  
 [<span data-ttu-id="445f8-188">レポート埋め込みデータセットと共有データセット &#40;レポートビルダーと SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="445f8-188">Report Embedded Datasets and Shared Datasets &#40;Report Builder and SSRS&#41;</span></span>](report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)  
 <span data-ttu-id="445f8-189">埋め込みデータセットと共有データセットについて説明します。</span><span class="sxs-lookup"><span data-stu-id="445f8-189">Provides information about embedded and shared datasets.</span></span>  
  
 [<span data-ttu-id="445f8-190">データセット フィールド コレクション &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="445f8-190">Dataset Fields Collection &#40;Report Builder and SSRS&#41;</span></span>](dataset-fields-collection-report-builder-and-ssrs.md)  
 <span data-ttu-id="445f8-191">クエリによって生成されるデータセット フィールド コレクションについて説明します。</span><span class="sxs-lookup"><span data-stu-id="445f8-191">Provides information about the dataset field collection generated by the query.</span></span>  
  
 [<span data-ttu-id="445f8-192">Reporting Services でサポートされるデータ ソース (SSRS)</span><span class="sxs-lookup"><span data-stu-id="445f8-192">Data Sources Supported by Reporting Services &#40;SSRS&#41;</span></span>](../create-deploy-and-manage-mobile-and-paginated-reports.md)  
 <span data-ttu-id="445f8-193">各データ拡張機能のプラットフォームおよびバージョン サポートに関する詳細な情報です。</span><span class="sxs-lookup"><span data-stu-id="445f8-193">Provides in-depth information about platform and version support for each data extension.</span></span>  
  
 
  
## <a name="see-also"></a><span data-ttu-id="445f8-194">参照</span><span class="sxs-lookup"><span data-stu-id="445f8-194">See Also</span></span>  
 <span data-ttu-id="445f8-195">[レポートパラメーター &#40;レポートビルダーとレポートデザイナー&#41;](../report-design/report-parameters-report-builder-and-report-designer.md) </span><span class="sxs-lookup"><span data-stu-id="445f8-195">[Report Parameters &#40;Report Builder and Report Designer&#41;](../report-design/report-parameters-report-builder-and-report-designer.md) </span></span>  
 <span data-ttu-id="445f8-196">[データのフィルター処理、グループ化、並べ替え &#40;レポートビルダーと SSRS&#41;](../report-design/filter-group-and-sort-data-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="445f8-196">[Filter, Group, and Sort Data &#40;Report Builder and SSRS&#41;](../report-design/filter-group-and-sort-data-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="445f8-197">式 &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="445f8-197">Expressions &#40;Report Builder and SSRS&#41;</span></span>](../report-design/expressions-report-builder-and-ssrs.md)  
  
  
