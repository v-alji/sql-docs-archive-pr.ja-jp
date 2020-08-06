---
title: 検索プロパティのプロパティ セット GUID およびプロパティ整数 ID の取得 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
helpviewer_keywords:
- full-text search [SQL Server], search property lists
- search property lists [SQL Server], configuring
ms.assetid: 7db79165-8bcc-4be6-8d40-12d44deda79f
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 53c08d3a2f86c7e412fbdb1caa6d55d7d23bf407
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87716206"
---
# <a name="find-property-set-guids-and-property-integer-ids-for-search-properties"></a><span data-ttu-id="2b473-102">検索プロパティのプロパティ セット GUID およびプロパティ整数 ID の取得</span><span class="sxs-lookup"><span data-stu-id="2b473-102">Find Property Set GUIDs and Property Integer IDs for Search Properties</span></span>
  <span data-ttu-id="2b473-103">このトピックでは、プロパティを検索プロパティ リストに追加してフルテキスト検索で検索できるようにするために事前に必要な値を取得する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="2b473-103">This topic discusses how to obtain the values that are required before you can add a property to a search property list and make it searchable by full-text search.</span></span> <span data-ttu-id="2b473-104">これらの値には、ドキュメント プロパティのプロパティ セット GUID およびプロパティ整数識別子が含まれます。</span><span class="sxs-lookup"><span data-stu-id="2b473-104">These values include the property set GUID and property integer identifier of a document property.</span></span>  
  
 <span data-ttu-id="2b473-105">バイナリデータから IFilters によって抽出されたドキュメントプロパティ `varbinary` `varbinary(max)` (、(を含む)、またはデータ型の列に格納されているデータ) は、 `FILESTREAM` `image` フルテキスト検索に使用できます。</span><span class="sxs-lookup"><span data-stu-id="2b473-105">Document properties that are extracted by IFilters from binary data - that is, from data stored in a `varbinary`, `varbinary(max)` (including `FILESTREAM`), or `image` data type column - can be made available for full-text search.</span></span> <span data-ttu-id="2b473-106">抽出されたプロパティを検索できるようにするには、検索プロパティ リストにプロパティを手動で追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2b473-106">To make an extracted property searchable, the property must be manually added to a search property list.</span></span> <span data-ttu-id="2b473-107">さらに、検索プロパティ リストを 1 つ以上のフルテキスト インデックスに関連付ける必要があります。</span><span class="sxs-lookup"><span data-stu-id="2b473-107">The search property list must also be associated with one or more full-text indexes.</span></span> <span data-ttu-id="2b473-108">詳細については、「 [検索プロパティ リストを使用したドキュメント プロパティの検索](search-document-properties-with-search-property-lists.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2b473-108">For more information, see [Search Document Properties with Search Property Lists](search-document-properties-with-search-property-lists.md).</span></span>  
  
 <span data-ttu-id="2b473-109">使用可能なプロパティをプロパティ リストに追加する前に、プロパティに関する以下の 2 つの情報を入手する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2b473-109">Before you can add an available property to a property list, you have to find 2 pieces of information about the property:</span></span>  
  
-   <span data-ttu-id="2b473-110">プロパティのプロパティ セット GUID</span><span class="sxs-lookup"><span data-stu-id="2b473-110">The property set GUID of the property.</span></span>  
  
-   <span data-ttu-id="2b473-111">プロパティの整数 ID</span><span class="sxs-lookup"><span data-stu-id="2b473-111">The integer ID of the property.</span></span>  
  
 <span data-ttu-id="2b473-112">プロパティ リストにプロパティを追加するとき、名前と説明も指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2b473-112">(When you add a property to a property list, you also have to provide a name and description.</span></span> <span data-ttu-id="2b473-113">ただし、プロパティの正規の名前と説明を使用する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="2b473-113">However you do not have to use the canonical name and description of the property.)</span></span>  
  
 <span data-ttu-id="2b473-114">このトピックでは、使用可能なプロパティ (特にマイクロソフトによって定義されているプロパティ) に関する情報を取得するための一般的な方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="2b473-114">This topic describes the commonly-used methods to find information about available properties, especially about properties that are defined by Microsoft.</span></span> <span data-ttu-id="2b473-115">サード パーティによって定義されているプロパティについては、サード パーティのドキュメントを参照するか、ベンダーに問い合わせてください。</span><span class="sxs-lookup"><span data-stu-id="2b473-115">For information about properties that have been defined by a third party, refer to the third-party documentation or contact the vendor.</span></span>  
  
##  <a name="finding-information-about-widely-used-well-known-microsoft-properties"></a><a name="wellknown"></a> <span data-ttu-id="2b473-116">広く使用され、知られている Microsoft プロパティについての情報の入手</span><span class="sxs-lookup"><span data-stu-id="2b473-116">Finding Information about Widely Used, Well-Known Microsoft Properties</span></span>  
 <span data-ttu-id="2b473-117">マイクロソフトでは、さまざまなコンテキストで使用できる何百ものドキュメント プロパティを定義していますが、それぞれのファイル形式で使用できるプロパティはごくわずかです。</span><span class="sxs-lookup"><span data-stu-id="2b473-117">Microsoft defines hundreds of document properties for use in many contexts, but only a small subset of the available properties are used by each file format.</span></span> <span data-ttu-id="2b473-118">頻繁に使用される Windows プロパティの中に、少数の汎用プロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="2b473-118">Among the frequently used Windows properties is a small set of generic properties.</span></span> <span data-ttu-id="2b473-119">よく知られている汎用プロパティの一部の例を次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="2b473-119">Some examples of well-known generic properties are shown in the following table.</span></span> <span data-ttu-id="2b473-120">この表では、よく知られている名前、Windows の正規名 (マイクロソフトが公開するプロパティの説明で使用)、プロパティ セット GUID、プロパティ整数識別子、および簡単な説明を示します。</span><span class="sxs-lookup"><span data-stu-id="2b473-120">The table shows the well-known name, the Windows canonical name (from the property description published by Microsoft), the property set GUID, the property integer identifier, and a brief description.</span></span>  
  
|<span data-ttu-id="2b473-121">よく知られている名前</span><span class="sxs-lookup"><span data-stu-id="2b473-121">Well-known name</span></span>|<span data-ttu-id="2b473-122">Windows の正規名</span><span class="sxs-lookup"><span data-stu-id="2b473-122">Windows canonical name</span></span>|<span data-ttu-id="2b473-123">プロパティ セット GUID</span><span class="sxs-lookup"><span data-stu-id="2b473-123">Property set GUID</span></span>|<span data-ttu-id="2b473-124">整数 ID</span><span class="sxs-lookup"><span data-stu-id="2b473-124">Integer ID</span></span>|<span data-ttu-id="2b473-125">説明</span><span class="sxs-lookup"><span data-stu-id="2b473-125">Description</span></span>|  
|----------------------|----------------------------|-----------------------|----------------|-----------------|  
|<span data-ttu-id="2b473-126">Authors</span><span class="sxs-lookup"><span data-stu-id="2b473-126">Authors</span></span>|`System.Author`|<span data-ttu-id="2b473-127">F29F85E0-4FF9-1068-AB91-08002B27B3D9</span><span class="sxs-lookup"><span data-stu-id="2b473-127">F29F85E0-4FF9-1068-AB91-08002B27B3D9</span></span>|<span data-ttu-id="2b473-128">4</span><span class="sxs-lookup"><span data-stu-id="2b473-128">4</span></span>|<span data-ttu-id="2b473-129">特定のアイテムの作成者。</span><span class="sxs-lookup"><span data-stu-id="2b473-129">Author or authors of a given item.</span></span>|  
|<span data-ttu-id="2b473-130">Tags</span><span class="sxs-lookup"><span data-stu-id="2b473-130">Tags</span></span>|`System.Keywords`|<span data-ttu-id="2b473-131">F29F85E0-4FF9-1068-AB91-08002B27B3D9</span><span class="sxs-lookup"><span data-stu-id="2b473-131">F29F85E0-4FF9-1068-AB91-08002B27B3D9</span></span>|<span data-ttu-id="2b473-132">5</span><span class="sxs-lookup"><span data-stu-id="2b473-132">5</span></span>|<span data-ttu-id="2b473-133">アイテムに割り当てられる一連のキーワード (タグとも呼ばれます)。</span><span class="sxs-lookup"><span data-stu-id="2b473-133">Set of keywords (also known as tags) assigned to the item.</span></span>|  
|<span data-ttu-id="2b473-134">Type</span><span class="sxs-lookup"><span data-stu-id="2b473-134">Type</span></span>|`System.PerceivedType`|<span data-ttu-id="2b473-135">28636AA6-953D-11D2-B5D6-00C04FD918D0</span><span class="sxs-lookup"><span data-stu-id="2b473-135">28636AA6-953D-11D2-B5D6-00C04FD918D0</span></span>|<span data-ttu-id="2b473-136">9</span><span class="sxs-lookup"><span data-stu-id="2b473-136">9</span></span>|<span data-ttu-id="2b473-137">正規の種類に基づいて認識されるファイルの種類。</span><span class="sxs-lookup"><span data-stu-id="2b473-137">Perceived file type based on its canonical type.</span></span>|  
|<span data-ttu-id="2b473-138">タイトル</span><span class="sxs-lookup"><span data-stu-id="2b473-138">Title</span></span>|`System.Title`|<span data-ttu-id="2b473-139">F29F85E0-4FF9-1068-AB91-08002B27B3D9</span><span class="sxs-lookup"><span data-stu-id="2b473-139">F29F85E0-4FF9-1068-AB91-08002B27B3D9</span></span>|<span data-ttu-id="2b473-140">2</span><span class="sxs-lookup"><span data-stu-id="2b473-140">2</span></span>|<span data-ttu-id="2b473-141">アイテムのタイトル。</span><span class="sxs-lookup"><span data-stu-id="2b473-141">Title of the item.</span></span> <span data-ttu-id="2b473-142">たとえば、ドキュメントのタイトル、メッセージの件名、写真のキャプション、または音楽トラックの名前。</span><span class="sxs-lookup"><span data-stu-id="2b473-142">For example, the title of a document, the subject of a message, the caption of a photo, or the name of a music track.</span></span>|  
  
 <span data-ttu-id="2b473-143">ファイル形式間で一貫性を保持するため、マイクロソフトでは、頻繁に使用される、優先度の高いドキュメントのプロパティのサブセットを、いくつかのドキュメントのカテゴリとして特定しています。</span><span class="sxs-lookup"><span data-stu-id="2b473-143">To encourage consistency among file formats, Microsoft has identified subsets of frequently used, high-priority document properties for several categories of documents.</span></span> <span data-ttu-id="2b473-144">これらには、通信、連絡先、ドキュメント、音楽ファイル、画像、およびビデオがあります。</span><span class="sxs-lookup"><span data-stu-id="2b473-144">These include communications, contacts, documents, music files, pictures, and videos.</span></span> <span data-ttu-id="2b473-145">各カテゴリの上位のプロパティの詳細については、Windows サーチに関するドキュメントの「 [カスタム ファイル形式のシステム定義プロパティ](https://go.microsoft.com/fwlink/?LinkId=144336) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2b473-145">For more information about the top-ranked properties for each category, see [system-defined properties for custom file formats](https://go.microsoft.com/fwlink/?LinkId=144336) in the Windows Search documentation.</span></span>  
  
 <span data-ttu-id="2b473-146">特定のファイル形式では、以下の 3 種類のプロパティが実装される場合があります。</span><span class="sxs-lookup"><span data-stu-id="2b473-146">A specific file format might implement properties of three types:</span></span>  
  
-   <span data-ttu-id="2b473-147">[!INCLUDE[msCoName](../../includes/msconame-md.md)]によって定義された汎用プロパティ</span><span class="sxs-lookup"><span data-stu-id="2b473-147">Generic properties defined by [!INCLUDE[msCoName](../../includes/msconame-md.md)].</span></span>  
  
-   <span data-ttu-id="2b473-148">[!INCLUDE[msCoName](../../includes/msconame-md.md)]によって定義された、カテゴリに固有のプロパティ</span><span class="sxs-lookup"><span data-stu-id="2b473-148">Category-specific properties defined by [!INCLUDE[msCoName](../../includes/msconame-md.md)].</span></span>  
  
-   <span data-ttu-id="2b473-149">ソフトウェア ベンダーによって定義された、アプリケーション固有のカスタム プロパティ</span><span class="sxs-lookup"><span data-stu-id="2b473-149">Custom, application-specific properties defined by the software vendor.</span></span>  
  
##  <a name="finding-information-about-available-properties-by-using-filtdumpexe"></a><a name="filtdump"></a><span data-ttu-id="2b473-150">FILTDUMP.EXE を使用して使用可能なプロパティに関する情報を検索する</span><span class="sxs-lookup"><span data-stu-id="2b473-150">Finding Information about Available Properties by using FILTDUMP.EXE</span></span>  
 <span data-ttu-id="2b473-151">インストールされた IFilter で検出および抽出されるプロパティを調べるには、 **Windows SDK に含まれている** filtdump.exe [!INCLUDE[msCoName](../../includes/msconame-md.md)] ユーティリティをインストールして実行してください。</span><span class="sxs-lookup"><span data-stu-id="2b473-151">To learn what properties are discovered and extracted by an installed IFilter, you can install and run the **filtdump.exe** utility, which is part of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows SDK.</span></span>  
  
 <span data-ttu-id="2b473-152">**filtdump.exe** はコマンド プロンプトから実行し、1 つの引数を指定します。</span><span class="sxs-lookup"><span data-stu-id="2b473-152">You run **filtdump.exe** from the command prompt and provide a single argument.</span></span> <span data-ttu-id="2b473-153">この引数は、インストールした IFilter が対象とする種類のファイルの個別の名前です。</span><span class="sxs-lookup"><span data-stu-id="2b473-153">This argument is the name of an individual file that has a file type for which an IFilter is installed.</span></span> <span data-ttu-id="2b473-154">このユーティリティは、IFilter で検出された、ドキュメント内のすべてのプロパティと、そのプロパティ セット GUID、整数 ID、および追加情報の一覧を表示します。</span><span class="sxs-lookup"><span data-stu-id="2b473-154">The utility displays a list of all the properties discovered by the IFilter in the document, with their property set GUIDs, integer IDs, and additional information.</span></span>  
  
 <span data-ttu-id="2b473-155">このソフトウェアをインストールする方法の詳細については、「 [Windows 7 および .NET Framework 4 用 Microsoft Windows SDK](https://www.microsoft.com/download/details.aspx?id=8279)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2b473-155">For information about installing this software, see [Microsoft Windows SDK for Windows 7 and .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=8279).</span></span> <span data-ttu-id="2b473-156">SDK をダウンロードしてインストールした後、以下のフォルダーで filtdump.exe ユーティリティを見つけてください。</span><span class="sxs-lookup"><span data-stu-id="2b473-156">After you download and install the SDK, look in the following folders for the filtdump.exe utility.</span></span>  
  
-   <span data-ttu-id="2b473-157">64 ビット バージョンの場合は、 `C:\Program Files\Microsoft SDKs\Windows\v7.1\Bin\x64`にあります。</span><span class="sxs-lookup"><span data-stu-id="2b473-157">For the 64-bit version, look in `C:\Program Files\Microsoft SDKs\Windows\v7.1\Bin\x64`.</span></span>  
  
-   <span data-ttu-id="2b473-158">32 ビット バージョンの場合は、 `C:\Program Files\Microsoft SDKs\Windows\v7.1\Bin`にあります。</span><span class="sxs-lookup"><span data-stu-id="2b473-158">For the 32-bit version, look in `C:\Program Files\Microsoft SDKs\Windows\v7.1\Bin`.</span></span>  
  
##  <a name="finding-values-for-a-search-property-from-a-windows-property-description"></a><a name="propdesc"></a><span data-ttu-id="2b473-159">Windows プロパティの説明からの検索プロパティの値の検索</span><span class="sxs-lookup"><span data-stu-id="2b473-159">Finding Values for a Search Property from a Windows Property Description</span></span>  
 <span data-ttu-id="2b473-160">よく知られた Windows 検索プロパティについては、プロパティの説明 (`formatID`) の `propID` 属性および `propertyDescription` 属性から必要な情報を入手できます。</span><span class="sxs-lookup"><span data-stu-id="2b473-160">For a well-known Windows search property, you can obtain the information that you need from the `formatID` and `propID` attributes of the property description (`propertyDescription`).</span></span>  
  
 <span data-ttu-id="2b473-161">次の例では、一般的なマイクロソフト プロパティの関連する部分 (この例では、 `System.Author` ) を示します。</span><span class="sxs-lookup"><span data-stu-id="2b473-161">The following example shows the relevant part of a typical Microsoft property description, in this case, of the `System.Author` property.</span></span> <span data-ttu-id="2b473-162">`formatID` 属性はプロパティ セット GUID の `F29F85E0-4FF9-1068-AB91-08002B27B3D9`を指定し、 `propID` 属性は、プロパティの整数 ID `4.` を指定します。 `name` 属性は、Windows の正規のプロパティ名である `System.Author`を示すことに注意してください</span><span class="sxs-lookup"><span data-stu-id="2b473-162">The `formatID` attribute specifies the property set GUID, `F29F85E0-4FF9-1068-AB91-08002B27B3D9`, and the `propID` attribute specifies the property integer ID, `4.` Notice that the `name` attribute specifies the Windows canonical property name, `System.Author`.</span></span> <span data-ttu-id="2b473-163">(この例では、関係のない列プロパティ説明部分を省略しています)。</span><span class="sxs-lookup"><span data-stu-id="2b473-163">(This example omits portions of the property description that are not relevant.)</span></span>  
  
```  
.  
propertyDescription  
name = System.Author  
...  
formatID = F29F85E0-4FF9-1068-AB91-08002B27B3D9  
propID = 4  
...  
```  
  
 <span data-ttu-id="2b473-164">このプロパティの完全な説明については、Windows サーチに関するドキュメントの「 [System.Author](https://go.microsoft.com/fwlink/?LinkId=144337) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2b473-164">For the complete description of this property, see [System.Author](https://go.microsoft.com/fwlink/?LinkId=144337) in the Windows Search documentation.</span></span>  
  
 <span data-ttu-id="2b473-165">Windows プロパティの完全な一覧については、Windows サーチに関するドキュメントの「 [Windows プロパティ](https://go.microsoft.com/fwlink/?LinkId=215013)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2b473-165">For a complete list of Windows properties, see [Windows Properties](https://go.microsoft.com/fwlink/?LinkId=215013), also in the Windows Search documentation.</span></span>  
  
##  <a name="adding-a-property-to-a-search-property-list"></a><a name="examples"></a><span data-ttu-id="2b473-166">検索プロパティリストへのプロパティの追加</span><span class="sxs-lookup"><span data-stu-id="2b473-166">Adding a Property to a Search Property List</span></span>  
 <span data-ttu-id="2b473-167">次の例では、プロパティを検索プロパティ リストに追加する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="2b473-167">The following example shows how to add a property to a search property list.</span></span> <span data-ttu-id="2b473-168">この例では、 [ALTER SEARCH PROPERTY LIST](/sql/t-sql/statements/alter-search-property-list-transact-sql) ステートメントを使用して、 `System.Author` プロパティを `PropertyList1`という名前の検索プロパティ リストに追加し、 `Author`という表示名を指定します。</span><span class="sxs-lookup"><span data-stu-id="2b473-168">The example uses an [ALTER SEARCH PROPERTY LIST](/sql/t-sql/statements/alter-search-property-list-transact-sql) statement to add the `System.Author` property to a search property list named `PropertyList1`, and provides a user friendly name for the property, `Author`.</span></span>  
  
```  
ALTER SEARCH PROPERTY LIST PropertyList1   
  ADD 'Author'  
    WITH (  
          PROPERTY_SET_GUID = 'F29F85E0-4FF9-1068-AB91-08002B27B3D9',  
          PROPERTY_INT_ID = 4,   
          PROPERTY_DESCRIPTION = 'System.Author - the author or authors of the item'   
         )  
GO  
```  
  
 <span data-ttu-id="2b473-169">検索プロパティ リストを作成し、フルテキスト インデックスに関連付ける方法については、「 [検索プロパティ リストを使用したドキュメント プロパティの検索](search-document-properties-with-search-property-lists.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2b473-169">For more information about creating a search property list and associating it with a full-text index, see [Search Document Properties with Search Property Lists](search-document-properties-with-search-property-lists.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b473-170">参照</span><span class="sxs-lookup"><span data-stu-id="2b473-170">See Also</span></span>  
 <span data-ttu-id="2b473-171">[検索プロパティリストを使用したドキュメントプロパティの検索](search-document-properties-with-search-property-lists.md) </span><span class="sxs-lookup"><span data-stu-id="2b473-171">[Search Document Properties with Search Property Lists](search-document-properties-with-search-property-lists.md) </span></span>  
 [<span data-ttu-id="2b473-172">検索用フィルターの構成と管理</span><span class="sxs-lookup"><span data-stu-id="2b473-172">Configure and Manage Filters for Search</span></span>](configure-and-manage-filters-for-search.md)  
  
  
