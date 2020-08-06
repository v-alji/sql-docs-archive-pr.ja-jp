---
title: RAW ファイル変換先 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.rawfiledest.f1
helpviewer_keywords:
- append options [Integration Services]
- destinations [Integration Services], Raw File
- raw data [Integration Services]
- writing raw data
- Raw File destination
ms.assetid: d311b458-aefc-4b4d-b1a1-4c0ebbb34214
author: chugugrace
ms.author: chugu
ms.openlocfilehash: fc5ce99be6e467ba323137ef885cbb13bfb328ce
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633921"
---
# <a name="raw-file-destination"></a><span data-ttu-id="d222e-102">RAW ファイル変換先 (Raw File destination)</span><span class="sxs-lookup"><span data-stu-id="d222e-102">Raw File Destination</span></span>
  <span data-ttu-id="d222e-103">RAW ファイル変換先は、生データをファイルに書き込みます。</span><span class="sxs-lookup"><span data-stu-id="d222e-103">The Raw File destination writes raw data to a file.</span></span> <span data-ttu-id="d222e-104">データは変換先に固有の形式であるため、データは変換の必要がなく、解析もほとんど必要ありません。</span><span class="sxs-lookup"><span data-stu-id="d222e-104">Because the format of the data is native to the destination, the data requires no translation and little parsing.</span></span> <span data-ttu-id="d222e-105">したがって、RAW ファイル変換先は、フラット ファイルや OLE DB 変換先などの他の変換先よりも、高速にデータを書き込むことができます。</span><span class="sxs-lookup"><span data-stu-id="d222e-105">This means that the Raw File destination can write data more quickly than other destinations such as the Flat File and the OLE DB destinations.</span></span>  
  
 <span data-ttu-id="d222e-106">RAW ファイル変換先を使用すると、RAW データをファイルに書き込むことに加え、パッケージを実行せずに、列のみを含む空の RAW ファイル (メタデータのみのファイル) を生成することができます。</span><span class="sxs-lookup"><span data-stu-id="d222e-106">In addition to writing raw data to a file, you can also use the Raw File destination to generate an empty raw file that contains only the columns (metadata-only file), without having to run the package.</span></span> <span data-ttu-id="d222e-107">以前に変換先によって書き込まれた RAW データを取得するには、RAW ファイル ソースを使用します。</span><span class="sxs-lookup"><span data-stu-id="d222e-107">You use the Raw File source to retrieve raw data that was previously written by the destination.</span></span> <span data-ttu-id="d222e-108">RAW ファイル ソースの参照先を、メタデータのみのファイルにすることもできます。</span><span class="sxs-lookup"><span data-stu-id="d222e-108">You can also point the Raw File source to the metadata-only file.</span></span>  
  
 <span data-ttu-id="d222e-109">RAW ファイルの形式には、並べ替えの情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="d222e-109">The raw file format contains sort information.</span></span> <span data-ttu-id="d222e-110">RAW ファイル変換先には、文字列の列の比較フラグを含む並べ替えの情報がすべて保存されます。</span><span class="sxs-lookup"><span data-stu-id="d222e-110">The Raw File Destination saves all the sort information including the comparison flags for string columns.</span></span> <span data-ttu-id="d222e-111">RAW ファイル ソースは、並べ替えの情報を読み取って受け入れます。</span><span class="sxs-lookup"><span data-stu-id="d222e-111">The Raw File source reads and honors the sort information.</span></span> <span data-ttu-id="d222e-112">詳細エディターを使用して、ファイル内の並べ替えのフラグを無視するように RAW ファイル ソースを構成するためのオプションが用意されています。</span><span class="sxs-lookup"><span data-stu-id="d222e-112">You do have the option of configuring the Raw File Source to ignore the sort flags in the file, using the Advanced Editor.</span></span> <span data-ttu-id="d222e-113">比較フラグの詳細については、「 [文字列データの比較](comparing-string-data.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d222e-113">For more information about comparison flags, see [Comparing String Data](comparing-string-data.md).</span></span>  
  
 <span data-ttu-id="d222e-114">RAW ファイル変換先は、次の方法で構成できます。</span><span class="sxs-lookup"><span data-stu-id="d222e-114">You can configure the Raw File destination in the following ways:</span></span>  
  
-   <span data-ttu-id="d222e-115">RAW ファイル変換先がデータを書き込むファイルの名前、またはその名前が含まれている変数のどちらかのアクセス モードを指定します。</span><span class="sxs-lookup"><span data-stu-id="d222e-115">Specify an access mode which is either the name of the file or a variable that contains the name of the file to which the Raw File destination writes.</span></span>  
  
-   <span data-ttu-id="d222e-116">RAW ファイル変換先によって、同じ名前の既存のファイルにデータを追加するか、新しいファイルを作成するかを指定します。</span><span class="sxs-lookup"><span data-stu-id="d222e-116">Indicate whether the Raw File destination appends data to an existing file that has the same name or creates a new file.</span></span>  
  
 <span data-ttu-id="d222e-117">RAW ファイル変換先は、パッケージの実行間で、部分的に処理されたデータの中間結果を書き込むために使用される場合がよくあります。</span><span class="sxs-lookup"><span data-stu-id="d222e-117">The Raw File destination is frequently used to write intermediary results of partly processed data between package executions.</span></span> <span data-ttu-id="d222e-118">生データを格納すると、RAW ファイル ソースによって迅速に読み取られたデータを、最終的な変換先に読み込む前に、さらに変換できます。</span><span class="sxs-lookup"><span data-stu-id="d222e-118">Storing raw data means that the data can be read quickly by a Raw File source and then further transformed before it is loaded into its final destination.</span></span> <span data-ttu-id="d222e-119">たとえば、パッケージを複数回実行し、そのたびに生データをファイルに書き込むことができます。</span><span class="sxs-lookup"><span data-stu-id="d222e-119">For example, a package might run several times, and each time write raw data to files.</span></span> <span data-ttu-id="d222e-120">後で、別のパッケージが RAW ファイル ソースを使用して各ファイルからデータを読み取り、全体結合変換を使用してデータを 1 つのデータセットにマージし、次に、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] テーブルなどの最後の変換先に読み込まれる前に、追加の変換を適用してデータを集約することができます。</span><span class="sxs-lookup"><span data-stu-id="d222e-120">Later, a different package can use the Raw File source to read from each file, use a Union All transformation to merge the data into one data set, and then apply additional transformations that summarize the data before loading the data into its final destination such as a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d222e-121">RAW ファイル変換先では、NULL データはサポートされていますが、バイナリ ラージ オブジェクト (BLOB) データはサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="d222e-121">The Raw File destination supports null data but not binary large object (BLOB) data.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d222e-122">RAW ファイル変換先は、接続マネージャーを使用しません。</span><span class="sxs-lookup"><span data-stu-id="d222e-122">The Raw File destination does not use a connection manager.</span></span>  
  
 <span data-ttu-id="d222e-123">この変換先は 1 つの標準入力をとります。</span><span class="sxs-lookup"><span data-stu-id="d222e-123">This source has one regular input.</span></span> <span data-ttu-id="d222e-124">エラー出力はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="d222e-124">It does not support an error output.</span></span>  
  
## <a name="append-and-new-file-options"></a><span data-ttu-id="d222e-125">データの追加および新しいファイルの作成オプション</span><span class="sxs-lookup"><span data-stu-id="d222e-125">Append and New File Options</span></span>  
 <span data-ttu-id="d222e-126">WriteOption プロパティには、データを既存のファイルに追加する、または新しいファイルを作成するオプションが含まれています。</span><span class="sxs-lookup"><span data-stu-id="d222e-126">The WriteOption property includes options to append data to an existing file or create a new file.</span></span>  
  
 <span data-ttu-id="d222e-127">次の表では、WriteOption プロパティで使用できるオプションについて説明します。</span><span class="sxs-lookup"><span data-stu-id="d222e-127">The following table describes the available options for the WriteOption property.</span></span>  
  
|<span data-ttu-id="d222e-128">オプション</span><span class="sxs-lookup"><span data-stu-id="d222e-128">Option</span></span>|<span data-ttu-id="d222e-129">説明</span><span class="sxs-lookup"><span data-stu-id="d222e-129">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="d222e-130">Append</span><span class="sxs-lookup"><span data-stu-id="d222e-130">Append</span></span>|<span data-ttu-id="d222e-131">既存のファイルにデータを追加します。</span><span class="sxs-lookup"><span data-stu-id="d222e-131">Appends data to an existing file.</span></span> <span data-ttu-id="d222e-132">追加するデータのメタデータは、ファイル形式と一致している必要があります。</span><span class="sxs-lookup"><span data-stu-id="d222e-132">The metadata of the appended data must match the file format.</span></span>|  
|<span data-ttu-id="d222e-133">常に作成する</span><span class="sxs-lookup"><span data-stu-id="d222e-133">Create always</span></span>|<span data-ttu-id="d222e-134">常に新しいファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="d222e-134">Always creates a new file.</span></span>|  
|<span data-ttu-id="d222e-135">1 回だけ作成する</span><span class="sxs-lookup"><span data-stu-id="d222e-135">Create once</span></span>|<span data-ttu-id="d222e-136">新しいファイルを 1 つ作成します。</span><span class="sxs-lookup"><span data-stu-id="d222e-136">Creates a new file.</span></span> <span data-ttu-id="d222e-137">ファイルが存在する場合、コンポーネントは失敗します。</span><span class="sxs-lookup"><span data-stu-id="d222e-137">If the file exists, the component fails.</span></span>|  
|<span data-ttu-id="d222e-138">切り捨てと追加</span><span class="sxs-lookup"><span data-stu-id="d222e-138">Truncate and append</span></span>|<span data-ttu-id="d222e-139">既存のファイルを切り捨て、データをそのファイルに書き込みます。</span><span class="sxs-lookup"><span data-stu-id="d222e-139">Truncates an existing file and then writes the data to the file.</span></span> <span data-ttu-id="d222e-140">追加するデータのメタデータは、ファイル形式と一致している必要があります。</span><span class="sxs-lookup"><span data-stu-id="d222e-140">The metadata of the appended data must match the file format.</span></span>|  
  
 <span data-ttu-id="d222e-141">データの追加に関する重要事項を次に示します。</span><span class="sxs-lookup"><span data-stu-id="d222e-141">The following are important items about appending data:</span></span>  
  
-   <span data-ttu-id="d222e-142">既存の RAW ファイルにデータを追加しても、データが再度並べ替えられることはありません。</span><span class="sxs-lookup"><span data-stu-id="d222e-142">Appending data to an existing raw file does not re-sort the data.</span></span>  
  
     <span data-ttu-id="d222e-143">並べ替えられるキーの順序が正しいことを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d222e-143">You need to make certain that the sorted keys remain in the correct order.</span></span>  
  
-   <span data-ttu-id="d222e-144">既存の RAW ファイルにデータを追加しても、ファイルのメタデータ (並べ替えの情報) が変更されることはありません。</span><span class="sxs-lookup"><span data-stu-id="d222e-144">Appending data to an existing raw file does not change the file metadata (sort information).</span></span>  
  
 <span data-ttu-id="d222e-145">たとえば、パッケージは ProductKey (PK) を基準に並べ替えられたデータを読み取ります。</span><span class="sxs-lookup"><span data-stu-id="d222e-145">For example, a package reads data sorted on the ProductKey (PK).</span></span> <span data-ttu-id="d222e-146">パッケージのデータ フローでは、既存の RAW ファイルにデータを追加します。</span><span class="sxs-lookup"><span data-stu-id="d222e-146">The package data flow appends the data to an existing raw file.</span></span> <span data-ttu-id="d222e-147">パッケージの初回実行時には、3 つの行 (PK 1000、1100、1200) を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="d222e-147">The first time the package runs, three rows are received (PK 1000, 1100, 1200).</span></span> <span data-ttu-id="d222e-148">RAW ファイルには次のデータが含まれています。</span><span class="sxs-lookup"><span data-stu-id="d222e-148">The raw file now contains the following data.</span></span>  
  
-   <span data-ttu-id="d222e-149">1000, productA</span><span class="sxs-lookup"><span data-stu-id="d222e-149">1000, productA</span></span>  
  
-   <span data-ttu-id="d222e-150">1100, productB</span><span class="sxs-lookup"><span data-stu-id="d222e-150">1100, productB</span></span>  
  
-   <span data-ttu-id="d222e-151">1200, productC</span><span class="sxs-lookup"><span data-stu-id="d222e-151">1200, productC</span></span>  
  
 <span data-ttu-id="d222e-152">パッケージの 2 回目の実行時には、2 つの新しい行 (PK 1001、1300) を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="d222e-152">The second time the package runs, two new rows are received (PK 1001, 1300).</span></span> <span data-ttu-id="d222e-153">RAW ファイルには次のデータが含まれています。</span><span class="sxs-lookup"><span data-stu-id="d222e-153">The raw file now contains the following data.</span></span>  
  
-   <span data-ttu-id="d222e-154">1000, productA</span><span class="sxs-lookup"><span data-stu-id="d222e-154">1000, productA</span></span>  
  
-   <span data-ttu-id="d222e-155">1100, productB</span><span class="sxs-lookup"><span data-stu-id="d222e-155">1100, productB</span></span>  
  
-   <span data-ttu-id="d222e-156">1200, productC</span><span class="sxs-lookup"><span data-stu-id="d222e-156">1200, productC</span></span>  
  
-   <span data-ttu-id="d222e-157">1001, productD</span><span class="sxs-lookup"><span data-stu-id="d222e-157">1001, productD</span></span>  
  
-   <span data-ttu-id="d222e-158">1300, productE</span><span class="sxs-lookup"><span data-stu-id="d222e-158">1300, productE</span></span>  
  
 <span data-ttu-id="d222e-159">新しいデータは RAW ファイルの末尾に追加されるため、並べ替えられるキー (PK) の順序が正しくありません。</span><span class="sxs-lookup"><span data-stu-id="d222e-159">The new data is appended to the end of the raw file, and the sorted keys (PK) are out of order.</span></span> <span data-ttu-id="d222e-160">また、追加操作ではファイルのメタデータ (並べ替えの情報) が変更されませんでした。</span><span class="sxs-lookup"><span data-stu-id="d222e-160">In addition, the append operation didn't change the file metadata (sort information).</span></span> <span data-ttu-id="d222e-161">RAW ファイル ソースを使用してファイルを読み取る場合、このコンポーネントは、ファイル内のデータの順序が正しくなくても PK を基準にファイルが並べ替えられることを示します。</span><span class="sxs-lookup"><span data-stu-id="d222e-161">If you read the file by using the Raw File source, the component indicates that the file is still sorted on PK even though the data in the file is no longer in the correct order.</span></span>  
  
 <span data-ttu-id="d222e-162">データの追加中でも並べ替えられるキーの順序を正しく保つために、パッケージのデータ フローを次の手順で作成できます。</span><span class="sxs-lookup"><span data-stu-id="d222e-162">To keep the sorted keys in the correct order while appending data, you can design the package data flow as follows:</span></span>  
  
1.  <span data-ttu-id="d222e-163">ソース A を使用して新しい行を取得します。</span><span class="sxs-lookup"><span data-stu-id="d222e-163">Retrieve new rows by using Source A.</span></span>  
  
2.  <span data-ttu-id="d222e-164">ソース B を使用して、RawFile1 から既存の行を取得します。</span><span class="sxs-lookup"><span data-stu-id="d222e-164">Retrieve existing rows from RawFile1 using Source B.</span></span>  
  
3.  <span data-ttu-id="d222e-165">全体結合変換を使用して、ソース A とソース B からの入力を結合します。</span><span class="sxs-lookup"><span data-stu-id="d222e-165">Combine the inputs from Source A and Source B by using the Union All transformation.</span></span>  
  
4.  <span data-ttu-id="d222e-166">PK を基準に並べ替えを行います。</span><span class="sxs-lookup"><span data-stu-id="d222e-166">Sort on PK.</span></span>  
  
5.  <span data-ttu-id="d222e-167">RAW ファイル変換先を使用して RawFile2 に書き込みます。</span><span class="sxs-lookup"><span data-stu-id="d222e-167">Write to RawFile2 by using the Raw File destination.</span></span>  
  
     <span data-ttu-id="d222e-168">データ フローにおいて、RawFile1 は読み取り元となるためロックされます。</span><span class="sxs-lookup"><span data-stu-id="d222e-168">RawFile1 is locked because it's being read from, in the data flow.</span></span>  
  
6.  <span data-ttu-id="d222e-169">RawFile1 を RawFile2 に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="d222e-169">Replace RawFile1 with RawFile2.</span></span>  
  
### <a name="using-the-raw-file-destination-in-a-loop"></a><span data-ttu-id="d222e-170">ループでの RAW ファイル変換先の使用</span><span class="sxs-lookup"><span data-stu-id="d222e-170">Using the Raw File Destination in a Loop</span></span>  
 <span data-ttu-id="d222e-171">RAW ファイル変換先を使用するデータ フローがループ内にある場合、ファイルを 1 回だけ作成し、ループが繰り返されるたびにデータをそのファイルに追加することができます。</span><span class="sxs-lookup"><span data-stu-id="d222e-171">If the data flow that uses the Raw File destination is in a loop, you may want to create the file once and then append data to the file when the loop repeats.</span></span> <span data-ttu-id="d222e-172">ファイルにデータを追加するには、追加するデータが既存のファイルの形式に一致している必要があります。</span><span class="sxs-lookup"><span data-stu-id="d222e-172">To append data to the file, the data that is appended must match the format of the existing file.</span></span>  
  
 <span data-ttu-id="d222e-173">ループの最初の繰り返しでファイルを作成し、ループの以降の繰り返しで行を追加するには、デザイン時に次のことを行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="d222e-173">To create the file in the first iteration of the loop, and then append rows in the subsequent iterations of the loop, you need to do the following at design time:</span></span>  
  
1.  <span data-ttu-id="d222e-174">WriteOption プロパティを **CreateOnce** または **CreateAlways**に設定し、ループの繰り返しを 1 回実行します。</span><span class="sxs-lookup"><span data-stu-id="d222e-174">Set the WriteOption property to **CreateOnce** or **CreateAlways**and run one iteration of the loop.</span></span> <span data-ttu-id="d222e-175">ファイルが作成されます。</span><span class="sxs-lookup"><span data-stu-id="d222e-175">The file is created.</span></span> <span data-ttu-id="d222e-176">これにより、追加するデータのメタデータとファイルが必ず一致するようになります。</span><span class="sxs-lookup"><span data-stu-id="d222e-176">This ensures that the metadata of appended data and the file matches.</span></span>  
  
2.  <span data-ttu-id="d222e-177">WriteOption プロパティ**をにリセットし、** ValidateExternalMetadata プロパティをに設定し `False` ます。</span><span class="sxs-lookup"><span data-stu-id="d222e-177">Reset the WriteOption property to **Append** and set the ValidateExternalMetadata property to `False`.</span></span>  
  
 <span data-ttu-id="d222e-178">**Append** オプションの代わりに **TruncateAppend** オプションを使用すると、以前の実行で追加された行が切り捨てられ、新しい行が追加されます。</span><span class="sxs-lookup"><span data-stu-id="d222e-178">If you use the **TruncateAppend** option instead of the **Append** option, it will truncate rows that were added in any previous iteration, and then append new rows.</span></span> <span data-ttu-id="d222e-179">また **TruncateAppend** オプションを使用するには、データがファイル形式に一致している必要があります。</span><span class="sxs-lookup"><span data-stu-id="d222e-179">Using the **TruncateAppend** option also requires that the data matches the file format.</span></span>  
  
## <a name="configuration-of-the-raw-file-destination"></a><span data-ttu-id="d222e-180">RAW ファイル変換先の構成</span><span class="sxs-lookup"><span data-stu-id="d222e-180">Configuration of the Raw File Destination</span></span>  
 <span data-ttu-id="d222e-181">プロパティを設定するには [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーから行うか、またはプログラムによって設定します。</span><span class="sxs-lookup"><span data-stu-id="d222e-181">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="d222e-182">**[詳細エディター]** ダイアログ ボックスには、プログラムによって設定できるプロパティが反映されます。</span><span class="sxs-lookup"><span data-stu-id="d222e-182">The **Advanced Editor** dialog box reflects the properties that can be set programmatically.</span></span> <span data-ttu-id="d222e-183">**[詳細エディター]** ダイアログ ボックスまたはプログラムで設定できるプロパティの詳細については、次のトピックのいずれかを参照してください。</span><span class="sxs-lookup"><span data-stu-id="d222e-183">For more information about the properties that you can set in the **Advanced Editor** dialog box or programmatically, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="d222e-184">Common Properties</span><span class="sxs-lookup"><span data-stu-id="d222e-184">Common Properties</span></span>](../common-properties.md)  
  
-   [<span data-ttu-id="d222e-185">RAW ファイルのカスタム プロパティ</span><span class="sxs-lookup"><span data-stu-id="d222e-185">Raw File Custom Properties</span></span>](raw-file-custom-properties.md)  
  
## <a name="related-tasks"></a><span data-ttu-id="d222e-186">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="d222e-186">Related Tasks</span></span>  
 <span data-ttu-id="d222e-187">コンポーネントのプロパティの設定方法の詳細については、「 [データ フロー コンポーネントのプロパティを設定する](set-the-properties-of-a-data-flow-component.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d222e-187">For information about how to set properties of the component, see [Set the Properties of a Data Flow Component](set-the-properties-of-a-data-flow-component.md).</span></span>  
  
## <a name="related-content"></a><span data-ttu-id="d222e-188">関連コンテンツ</span><span class="sxs-lookup"><span data-stu-id="d222e-188">Related Content</span></span>  
 <span data-ttu-id="d222e-189">sqlservercentral.com のブログ「 [RAW ファイルは最高](https://www.sqlservercentral.com/blogs/31-days-of-ssis-%e2%80%93-raw-files-are-awesome-131)」</span><span class="sxs-lookup"><span data-stu-id="d222e-189">Blog entry, [Raw Files Are Awesome](https://www.sqlservercentral.com/blogs/31-days-of-ssis-%e2%80%93-raw-files-are-awesome-131), on sqlservercentral.com.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d222e-190">参照</span><span class="sxs-lookup"><span data-stu-id="d222e-190">See Also</span></span>  
 <span data-ttu-id="d222e-191">[Raw ファイルソース](raw-file-source.md) </span><span class="sxs-lookup"><span data-stu-id="d222e-191">[Raw File Source](raw-file-source.md) </span></span>  
 [<span data-ttu-id="d222e-192">データ フロー</span><span class="sxs-lookup"><span data-stu-id="d222e-192">Data Flow</span></span>](data-flow.md)  
  
  
