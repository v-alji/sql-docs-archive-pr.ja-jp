---
title: IBCPSession::BCPInit (OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- IBCPSession::BCPInit (OLE DB)
topic_type:
- apiref
helpviewer_keywords:
- BCPInit method
ms.assetid: 583096d7-da34-49be-87fd-31210aac81aa
author: rothja
ms.author: jroth
ms.openlocfilehash: 25a01c71811de9d47ce01714402460bb53d4c70e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87714313"
---
# <a name="ibcpsessionbcpinit-ole-db"></a><span data-ttu-id="c4662-102">IBCPSession::BCPInit (OLE DB)</span><span class="sxs-lookup"><span data-stu-id="c4662-102">IBCPSession::BCPInit (OLE DB)</span></span>
  <span data-ttu-id="c4662-103">一括コピー構造を初期化し、エラー チェックを実行して、データ ファイルとフォーマット ファイルの名前が正しいことを確認します。その後、それらのファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="c4662-103">Initializes the bulk copy structure, performs some error checking, verifies that the data and format file names are correct, and then opens them.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c4662-104">構文</span><span class="sxs-lookup"><span data-stu-id="c4662-104">Syntax</span></span>  
  
```  
  
HRESULT BCPInit(   
const wchar_t *pwszTable,  
const wchar_t *pwszDataFile,  
const wchar_t *pwszErrorFile,  
inteDirection);  
```  
  
## <a name="remarks"></a><span data-ttu-id="c4662-105">解説</span><span class="sxs-lookup"><span data-stu-id="c4662-105">Remarks</span></span>  
 <span data-ttu-id="c4662-106">**BCPInit** メソッドは、他のすべての一括コピー メソッドの前に呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="c4662-106">The **BCPInit** method should be called before any other bulk-copy method.</span></span> <span data-ttu-id="c4662-107">**BCPInit** メソッドにより、ワークステーションと [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] との間のデータの一括コピーに必要な初期化が実行されます。</span><span class="sxs-lookup"><span data-stu-id="c4662-107">The **BCPInit** method performs the necessary initializations for a bulk copy of data between the workstation and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="c4662-108">**BCPInit** メソッドは、データ ファイルではなく、データベースのコピー元テーブルまたはコピー先テーブルの構造を調べます。</span><span class="sxs-lookup"><span data-stu-id="c4662-108">The **BCPInit** method examines the structure of the database source or target table, not the data file.</span></span> <span data-ttu-id="c4662-109">また、データベース テーブル、ビュー、または SELECT 結果セット内の各列に基づいてデータ ファイルのデータ形式値を指定します。</span><span class="sxs-lookup"><span data-stu-id="c4662-109">It specifies data format values for the data file based on each column in the database table, view, or SELECT result set.</span></span> <span data-ttu-id="c4662-110">このデータ形式値には、各列のデータ型、長さや NULL のインジケーターとターミネータのバイト文字列がデータ内に存在するかどうか、および固定長データ型の幅の指定などが含まれます。</span><span class="sxs-lookup"><span data-stu-id="c4662-110">This specification includes the data type of each column, the presence or absence of a length or null indicator and terminator byte strings in the data, and the width of fixed-length data types.</span></span> <span data-ttu-id="c4662-111">**BCPInit** メソッドでは、これらの値を次のように設定します。</span><span class="sxs-lookup"><span data-stu-id="c4662-111">The **BCPInit** method sets these values as follows:</span></span>  
  
-   <span data-ttu-id="c4662-112">指定するデータ型は、データベース テーブル、ビュー、または SELECT 結果セット内の列のデータ型です。</span><span class="sxs-lookup"><span data-stu-id="c4662-112">The data type specified is the data type of the column in the database table, view, or SELECT result set.</span></span> <span data-ttu-id="c4662-113">データ型は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] native Client ヘッダーファイル (sqlncli) で指定されたネイティブデータ型によって列挙されます。</span><span class="sxs-lookup"><span data-stu-id="c4662-113">The data type is enumerated by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] native data types specified in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client header file (sqlncli.h).</span></span> <span data-ttu-id="c4662-114">列挙される値の形式は、BCP_TYPE_XXX です。</span><span class="sxs-lookup"><span data-stu-id="c4662-114">Their values are in the pattern of BCP_TYPE_XXX.</span></span> <span data-ttu-id="c4662-115">データはそのコンピューターの形式で表されます。</span><span class="sxs-lookup"><span data-stu-id="c4662-115">The data is represented in its computer form.</span></span> <span data-ttu-id="c4662-116">つまり、integer データ型の列のデータは、データ ファイルを作成したコンピューターに基づいて、ビッグ エンディアンまたはリトル エンディアンの 4 バイト シーケンスで表されます。</span><span class="sxs-lookup"><span data-stu-id="c4662-116">That is, data from a column of integer data type is represented by a four-byte sequence that is big-or little-endian based on the computer that created the data file.</span></span>  
  
-   <span data-ttu-id="c4662-117">データベースのデータ型が固定長の場合は、データ ファイルのデータも固定長になります。</span><span class="sxs-lookup"><span data-stu-id="c4662-117">If a database data type is fixed in length, the data file data is also fixed in length.</span></span> <span data-ttu-id="c4662-118">データを処理する一括コピー メソッド ([IBCPSession::BCPExec](ibcpsession-bcpexec-ole-db.md) など) では、データ行が解析されます。データ ファイル内のデータの長さは、データベース テーブル、ビュー、または SELECT 列リスト内で指定されるデータの長さと同じでなければなりません。</span><span class="sxs-lookup"><span data-stu-id="c4662-118">Bulk-copy methods that process data (for example, [IBCPSession::BCPExec](ibcpsession-bcpexec-ole-db.md)) parse data rows expecting the length of the data in the data file to be identical to the length of the data specified in the database table, view, or SELECT column list.</span></span> <span data-ttu-id="c4662-119">たとえば、`char(13)` で定義されているデータベース列のデータは、ファイル内の各データ行に 13 文字で表す必要があります。</span><span class="sxs-lookup"><span data-stu-id="c4662-119">For example, data for a database column defined as `char(13)` must be represented by 13 characters for each row of data in the file.</span></span> <span data-ttu-id="c4662-120">データベース列で NULL 値を許容する場合は、固定長データにプレフィックスとして NULL インジケーターを付けることができます。</span><span class="sxs-lookup"><span data-stu-id="c4662-120">Fixed-length data can be prefixed with a null indicator if the database column allows null values.</span></span>  
  
-   <span data-ttu-id="c4662-121">データを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] にコピーするときは、データ ファイルにデータベース テーブル内の各列に格納するデータが含まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="c4662-121">When copying data to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], the data file must have data for each column in the database table.</span></span> <span data-ttu-id="c4662-122">データを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] からコピーするときは、データベース テーブル、ビュー、または SELECT 結果セット内のすべての列のデータがデータ ファイルにコピーされます。</span><span class="sxs-lookup"><span data-stu-id="c4662-122">When copying data from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], data from all columns in the database table, view, or SELECT result set are copied to the data file.</span></span>  
  
-   <span data-ttu-id="c4662-123">データを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] にコピーするときは、データ ファイル内の列の序数位置がデータベース テーブル内の列の序数位置と同じであることが必要です。</span><span class="sxs-lookup"><span data-stu-id="c4662-123">When copying data to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], the ordinal position of a column in the data file must be identical to the ordinal position of the column in the database table.</span></span> <span data-ttu-id="c4662-124">データを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] からコピーするときは、**BCPExec** メソッドによりデータベース テーブル内の列の序数位置に基づいてデータが配置されます。</span><span class="sxs-lookup"><span data-stu-id="c4662-124">When copying data from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], the **BCPExec** method places data based on the ordinal position of the column in the database table.</span></span>  
  
-   <span data-ttu-id="c4662-125">データベースのデータ型が可変長 (`varbinary(22)` など) の場合、またはデータベース列に NULL 値を格納できる場合は、データ ファイル内のデータにプレフィックスとして長さのインジケーターや NULL インジケーターを付けることができます。</span><span class="sxs-lookup"><span data-stu-id="c4662-125">If a database data type is variable in length (for example, `varbinary(22)`) or if a database column can contain null values, data in the data file is prefixed by a length/null indicator.</span></span> <span data-ttu-id="c4662-126">インジケーターの幅は、データ型と一括コピーのバージョンによって異なります。</span><span class="sxs-lookup"><span data-stu-id="c4662-126">The width of the indicator varies based on the data type and version of bulk copy.</span></span> <span data-ttu-id="c4662-127">[IBCPSession::BCPControl](ibcpsession-bcpcontrol-ole-db.md) メソッドのオプションである BCP_OPTION_FILEFMT では、データ内のインジケーターの幅が必要な幅より狭くなる時点を示すことで、以前の一括コピー データ ファイルと最新バージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を実行しているサーバーとの間の互換性を確保しています。</span><span class="sxs-lookup"><span data-stu-id="c4662-127">The [IBCPSession::BCPControl](ibcpsession-bcpcontrol-ole-db.md) method option BCP_OPTION_FILEFMT provides compatibility between earlier bulk-copy data files and servers running later versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] by indicating when the width of indicators in the data is narrower than expected.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c4662-128">データ ファイルに指定したデータ形式値を変更するには、[IBCPSession::BCPColumns](ibcpsession-bcpcolumns-ole-db.md) メソッドと [IBCPSession::BCPColFmt](ibcpsession-bcpcolfmt-ole-db.md) メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="c4662-128">To change the data format values specified for a data file, use the [IBCPSession::BCPColumns](ibcpsession-bcpcolumns-ole-db.md) and [IBCPSession::BCPColFmt](ibcpsession-bcpcolfmt-ole-db.md) methods.</span></span>  
  
 <span data-ttu-id="c4662-129">テーブルにインデックスが含まれていない場合は、データベース オプション **select into/bulkcopy** を設定することにより、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] への一括コピーを最適化できます。</span><span class="sxs-lookup"><span data-stu-id="c4662-129">Bulk copies to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] can be optimized for tables that do not contain indexes by setting the database option **select into/bulkcopy**.</span></span>  
  
## <a name="arguments"></a><span data-ttu-id="c4662-130">引数</span><span class="sxs-lookup"><span data-stu-id="c4662-130">Arguments</span></span>  
 <span data-ttu-id="c4662-131">*pwszTable*[in]</span><span class="sxs-lookup"><span data-stu-id="c4662-131">*pwszTable*[in]</span></span>  
 <span data-ttu-id="c4662-132">コピー操作の対象になるデータベース テーブルの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="c4662-132">The name of the database table to be copied into or out of.</span></span> <span data-ttu-id="c4662-133">名前には、データベース名や所有者名を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="c4662-133">The name can include the database name or the owner name.</span></span> <span data-ttu-id="c4662-134">たとえば、"pubs.username.titles"、"pubs..titles"、"username.titles" のように指定できます。</span><span class="sxs-lookup"><span data-stu-id="c4662-134">For example, "pubs.username.titles", "pubs..titles", "username.titles".</span></span>  
  
 <span data-ttu-id="c4662-135">eDirection 引数を BCP_DIRECTION_OUT に設定すると、pwszTable 引数をデータベース ビューの名前にすることができます。</span><span class="sxs-lookup"><span data-stu-id="c4662-135">If the eDirection argument is set to BCP_DIRECTION_OUT, the pwszTable argument can be the name of a database view.</span></span>  
  
 <span data-ttu-id="c4662-136">eDirection 引数を BCP_DIRECTION_OUT に設定し、**BCPExec** メソッドを呼び出す前に **BCPControl** メソッドを使用して SELECT ステートメントを指定する場合は、*pwszTable* 引数に NULL を設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c4662-136">If the eDirection argument is set to BCP_DIRECTION_OUT and a SELECT statement is specified using the **BCPControl** method before the **BCPExec** method is called, the *pwszTable* argument must be set to NULL.</span></span>  
  
 <span data-ttu-id="c4662-137">*pwszDataFile*[in]</span><span class="sxs-lookup"><span data-stu-id="c4662-137">*pwszDataFile*[in]</span></span>  
 <span data-ttu-id="c4662-138">コピー操作の対象になるユーザー ファイルの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="c4662-138">The name of the user file to be copied into or out of.</span></span>  
  
 <span data-ttu-id="c4662-139">*pwszErrorFile*[in]</span><span class="sxs-lookup"><span data-stu-id="c4662-139">*pwszErrorFile*[in]</span></span>  
 <span data-ttu-id="c4662-140">進行状況メッセージ、エラー メッセージ、およびユーザー ファイルからテーブルにコピーできなかった行のコピーを格納するエラー ファイルの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="c4662-140">The name of the error file to be filled with progress messages, error messages, and copies of any rows that could not be copied from a user file to a table.</span></span> <span data-ttu-id="c4662-141">*pwszErrorFile* 引数に NULL を設定すると、エラー ファイルが使用されません。</span><span class="sxs-lookup"><span data-stu-id="c4662-141">If the *pwszErrorFile* argument is set to NULL, no error file is used.</span></span>  
  
 <span data-ttu-id="c4662-142">*eDirection*[in]</span><span class="sxs-lookup"><span data-stu-id="c4662-142">*eDirection*[in]</span></span>  
 <span data-ttu-id="c4662-143">コピー操作の方向として、BCP_DIRECTION_IN か BCP_DIRECTION _OUT のいずれかを設定します。</span><span class="sxs-lookup"><span data-stu-id="c4662-143">The direction of the copy operation, either BCP_DIRECTION_IN or BCP_DIRECTION _OUT.</span></span> <span data-ttu-id="c4662-144">BCP_DIRECTION _IN はユーザー ファイルからデータベース テーブルへのコピーを示します。BCP_DIRECTION _OUT はデータベース テーブルからユーザー ファイルへのコピーを示します。</span><span class="sxs-lookup"><span data-stu-id="c4662-144">BCP_DIRECTION _IN indicates a copy from a user file to a database table; BCP_DIRECTION _OUT indicates a copy from a database table to a user file.</span></span>  
  
## <a name="return-code-values"></a><span data-ttu-id="c4662-145">リターン コードの値</span><span class="sxs-lookup"><span data-stu-id="c4662-145">Return Code Values</span></span>  
 <span data-ttu-id="c4662-146">S_OK</span><span class="sxs-lookup"><span data-stu-id="c4662-146">S_OK</span></span>  
 <span data-ttu-id="c4662-147">メソッドが成功しました。</span><span class="sxs-lookup"><span data-stu-id="c4662-147">The method succeeded.</span></span>  
  
 <span data-ttu-id="c4662-148">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="c4662-148">E_FAIL</span></span>  
 <span data-ttu-id="c4662-149">プロバイダー固有のエラーが発生しました。詳細については、 [ISQLServerErrorInfo](../../database-engine/dev-guide/isqlservererrorinfo-ole-db.md)インターフェイスを使用してください。</span><span class="sxs-lookup"><span data-stu-id="c4662-149">A provider specific error occurred' for detailed information, use the [ISQLServerErrorInfo](../../database-engine/dev-guide/isqlservererrorinfo-ole-db.md) interface.</span></span>  
  
 <span data-ttu-id="c4662-150">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="c4662-150">E_OUTOFMEMORY</span></span>  
 <span data-ttu-id="c4662-151">メモリ不足エラーです。</span><span class="sxs-lookup"><span data-stu-id="c4662-151">Out-of-memory error.</span></span>  
  
 <span data-ttu-id="c4662-152">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="c4662-152">E_INVALIDARG</span></span>  
 <span data-ttu-id="c4662-153">1 つ以上の引数が正しく指定されませんでした。</span><span class="sxs-lookup"><span data-stu-id="c4662-153">One or more of the arguments was not correctly specified.</span></span> <span data-ttu-id="c4662-154">たとえば、無効なファイル名が指定されました。</span><span class="sxs-lookup"><span data-stu-id="c4662-154">For example, an invalid file name was given.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4662-155">参照</span><span class="sxs-lookup"><span data-stu-id="c4662-155">See Also</span></span>  
 <span data-ttu-id="c4662-156">[IBCPSession &#40;OLE DB&#41;](ibcpsession-ole-db.md) </span><span class="sxs-lookup"><span data-stu-id="c4662-156">[IBCPSession &#40;OLE DB&#41;](ibcpsession-ole-db.md) </span></span>  
 [<span data-ttu-id="c4662-157">一括コピー操作の実行</span><span class="sxs-lookup"><span data-stu-id="c4662-157">Performing Bulk Copy Operations</span></span>](../native-client/features/performing-bulk-copy-operations.md)  
  
  
