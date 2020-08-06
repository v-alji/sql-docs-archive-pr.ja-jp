---
title: IBCPSession::BCPColFmt (OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- IBCPSession::BCPColFmt (OLE DB)
topic_type:
- apiref
helpviewer_keywords:
- BCPColFmt method
ms.assetid: 2852f4ba-f1c6-4c4c-86b2-b77e4abe70de
author: rothja
ms.author: jroth
ms.openlocfilehash: d60fa5dc93473f477926719cdcc05d13e72d8fd1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739829"
---
# <a name="ibcpsessionbcpcolfmt-ole-db"></a><span data-ttu-id="fc0e1-102">IBCPSession::BCPColFmt (OLE DB)</span><span class="sxs-lookup"><span data-stu-id="fc0e1-102">IBCPSession::BCPColFmt (OLE DB)</span></span>
  <span data-ttu-id="fc0e1-103">プログラム変数と [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 列のバインドを作成します。</span><span class="sxs-lookup"><span data-stu-id="fc0e1-103">Creates a binding between program variables and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] columns.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fc0e1-104">構文</span><span class="sxs-lookup"><span data-stu-id="fc0e1-104">Syntax</span></span>  
  
```  
  
HRESULT BCPColFmt(   
DBORDINALidxUserDataCol,  
inteUserDataType,  
intcbIndicator,  
intcbUserData,  
BYTE *pbUserDataTerm,  
intcbUserDataTerm,  
DBORDINALidxServerCol);  
```  
  
## <a name="remarks"></a><span data-ttu-id="fc0e1-105">解説</span><span class="sxs-lookup"><span data-stu-id="fc0e1-105">Remarks</span></span>  
 <span data-ttu-id="fc0e1-106">**BCPColFmt** メソッドは、BCP データ ファイルのフィールドと [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 列のバインドを作成するために使用します。</span><span class="sxs-lookup"><span data-stu-id="fc0e1-106">The **BCPColFmt** method is used to create a binding between BCP data file fields and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] columns.</span></span> <span data-ttu-id="fc0e1-107">このメソッドは、列の長さ、型、ターミネータ、およびプレフィックス長をパラメーターとして受け取り、個々のフィールドの対応するプロパティに設定します。</span><span class="sxs-lookup"><span data-stu-id="fc0e1-107">It takes in the length, type, terminator, and prefix length of a column as parameters and sets each of these properties for individual fields.</span></span>  
  
 <span data-ttu-id="fc0e1-108">ユーザーが対話モードを選択すると、このメソッドが 2 回呼び出されます。1 回は既定値 (サーバーの列の型によって異なります) に応じて列形式を設定するために呼び出され、もう 1 回はクライアントが対話モードで選択した列の型に応じて各列の形式を設定するために呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="fc0e1-108">If the user chooses interactive mode, this method is called twice; once to set the column format according to the default values (which are according to the type of the server column), and once to set the format according to the column type of the choice of the client chosen during interactive mode, for each column.</span></span>  
  
 <span data-ttu-id="fc0e1-109">対話モード以外の場合、このメソッドは列ごとに 1 回だけ呼び出され、各列の型を文字型またはネイティブ型に設定し、列ターミネータと行ターミネータを設定します。</span><span class="sxs-lookup"><span data-stu-id="fc0e1-109">In non-interactive modes, it is called only once per column to set the type of each column to character or native type, and to set the column and row terminators.</span></span>  
  
 <span data-ttu-id="fc0e1-110">**BCPColFmt** メソッドにより、一括コピーのユーザー ファイル形式を指定できます。</span><span class="sxs-lookup"><span data-stu-id="fc0e1-110">The **BCPColFmt** method allows you to specify the user-file format for bulk copies.</span></span> <span data-ttu-id="fc0e1-111">次に、一括コピーに使用するフォーマットの内容を示します。</span><span class="sxs-lookup"><span data-stu-id="fc0e1-111">For bulk copy, a format contains the following parts:</span></span>  
  
-   <span data-ttu-id="fc0e1-112">ユーザー ファイルのフィールドからデータベース列へのマッピング</span><span class="sxs-lookup"><span data-stu-id="fc0e1-112">A mapping from user-file fields to database columns.</span></span>  
  
-   <span data-ttu-id="fc0e1-113">ユーザー ファイルの各フィールドのデータ型</span><span class="sxs-lookup"><span data-stu-id="fc0e1-113">The data type of each user-file field.</span></span>  
  
-   <span data-ttu-id="fc0e1-114">各フィールドの省略可能なインジケーターの長さ</span><span class="sxs-lookup"><span data-stu-id="fc0e1-114">The length of the optional indicator for each field.</span></span>  
  
-   <span data-ttu-id="fc0e1-115">ユーザー ファイルの各フィールドにおけるデータの最大長</span><span class="sxs-lookup"><span data-stu-id="fc0e1-115">The maximum length of data per user-file field.</span></span>  
  
-   <span data-ttu-id="fc0e1-116">各フィールドの省略可能なターミネータ バイト シーケンス</span><span class="sxs-lookup"><span data-stu-id="fc0e1-116">The optional terminating byte sequence for each field.</span></span>  
  
-   <span data-ttu-id="fc0e1-117">省略可能なターミネータ バイト シーケンスの長さ</span><span class="sxs-lookup"><span data-stu-id="fc0e1-117">The length of the optional terminating byte sequence.</span></span>  
  
 <span data-ttu-id="fc0e1-118">**BCPColFmt** を呼び出すたびに、ユーザー ファイルの 1 つのフィールドの形式が指定されます。</span><span class="sxs-lookup"><span data-stu-id="fc0e1-118">Each call to **BCPColFmt** specifies the format for one user-file field.</span></span> <span data-ttu-id="fc0e1-119">たとえば、5 つのフィールドから構成されるユーザー データ ファイルの 3 つのフィールドの既定の設定を変更するには、まず、`BCPColumns(5)` を呼び出し、**BCPColFmt** を 5 回呼び出します。この 5 回の呼び出しのうち 3 回は独自の形式を設定して呼び出します。</span><span class="sxs-lookup"><span data-stu-id="fc0e1-119">For example, to change the default settings for three fields in a five-field user data file, first call `BCPColumns(5)`, and then call **BCPColFmt** five times, with three of those calls setting your custom format.</span></span> <span data-ttu-id="fc0e1-120">残りの 2 回の呼び出しでは、*eUserDataType* を BCP_TYPE_DEFAULT に設定し、*cbIndicator*、*cbUserData*、*cbUserDataTerm* をそれぞれ 0、BCP_VARIABLE_LENGTH、0 に設定します。</span><span class="sxs-lookup"><span data-stu-id="fc0e1-120">For the remaining two calls, set *eUserDataType* to BCP_TYPE_DEFAULT, and set *cbIndicator*, *cbUserData*, and *cbUserDataTerm* to 0, BCP_VARIABLE_LENGTH, and 0 respectively.</span></span> <span data-ttu-id="fc0e1-121">このプロシージャでは、5 つの列すべてをコピーします。それらの列のうち 3 つはカスタマイズされた形式でコピーされ、2 つは既定の形式でコピーされます。</span><span class="sxs-lookup"><span data-stu-id="fc0e1-121">This procedure copies all five columns, three with your customized format and two with the default format.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="fc0e1-122">**BCPColFmt** を呼び出す前に、[IBCPSession::BCPColumns](ibcpsession-bcpcolumns-ole-db.md) メソッドを呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="fc0e1-122">The [IBCPSession::BCPColumns](ibcpsession-bcpcolumns-ole-db.md) method must be called before any calls to **BCPColFmt**.</span></span> <span data-ttu-id="fc0e1-123">**BCPColFmt** は、ユーザー ファイル内の列ごとに 1 回呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="fc0e1-123">You must call **BCPColFmt** once for each column in the user file.</span></span> <span data-ttu-id="fc0e1-124">**BCPColFmt** をユーザー ファイルの任意の列に対して複数回呼び出すと、エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="fc0e1-124">Calling **BCPColFmt** more than once for any user-file column causes an error.</span></span>  
  
 <span data-ttu-id="fc0e1-125">ユーザー ファイル内の全データを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] テーブルにコピーする必要はありません。</span><span class="sxs-lookup"><span data-stu-id="fc0e1-125">You do not have to copy all of the data in a user file to a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table.</span></span> <span data-ttu-id="fc0e1-126">列をスキップするには、列のデータの形式を指定する際に idxServerCol パラメーターを 0 に設定します。</span><span class="sxs-lookup"><span data-stu-id="fc0e1-126">To skip a column, specify the format of the data for the column setting the idxServerCol parameter to 0.</span></span> <span data-ttu-id="fc0e1-127">一方、フィールドをスキップする場合は、メソッドを正しく機能させるためにすべての情報が必要になります。</span><span class="sxs-lookup"><span data-stu-id="fc0e1-127">In order to skip a field, you still need all the information for the method to work correctly.</span></span>  
  
 <span data-ttu-id="fc0e1-128">**注**[IBCPSession::BCPWriteFmt](ibcpsession-bcpwritefmt-ole-db.md) 関数を使用すると、**BCPColFmt** で指定された形式指定を保存できます。</span><span class="sxs-lookup"><span data-stu-id="fc0e1-128">**Note** The [IBCPSession::BCPWriteFmt](ibcpsession-bcpwritefmt-ole-db.md) function can be used to persist the format specification provided through **BCPColFmt**.</span></span>  
  
## <a name="arguments"></a><span data-ttu-id="fc0e1-129">引数</span><span class="sxs-lookup"><span data-stu-id="fc0e1-129">Arguments</span></span>  
 <span data-ttu-id="fc0e1-130">*idxUserDataCol*[in]</span><span class="sxs-lookup"><span data-stu-id="fc0e1-130">*idxUserDataCol*[in]</span></span>  
 <span data-ttu-id="fc0e1-131">ユーザー データ ファイル内のフィールドのインデックス。</span><span class="sxs-lookup"><span data-stu-id="fc0e1-131">Index of field in the user's data file.</span></span>  
  
 <span data-ttu-id="fc0e1-132">*eUserDataType*[in]</span><span class="sxs-lookup"><span data-stu-id="fc0e1-132">*eUserDataType*[in]</span></span>  
 <span data-ttu-id="fc0e1-133">ユーザー データ ファイル内のフィールドのデータ型。</span><span class="sxs-lookup"><span data-stu-id="fc0e1-133">The data type of field in the user's data file.</span></span> <span data-ttu-id="fc0e1-134">使用できるデータ型は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ヘッダーファイル (sqlncli) に、BCP_TYPE_SQLINT4 などの BCP_TYPE_XXX 形式で一覧表示されます。</span><span class="sxs-lookup"><span data-stu-id="fc0e1-134">The data types available are listed in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client header file (sqlncli.h) with BCP_TYPE_XXX format, for example, BCP_TYPE_SQLINT4.</span></span> <span data-ttu-id="fc0e1-135">BCP_TYPE_DEFAULT 値を指定すると、プロバイダーはテーブルやビューの列と同じ型を使用します。</span><span class="sxs-lookup"><span data-stu-id="fc0e1-135">If the BCP_TYPE_DEFAULT value is specified, the provider tries to use the same type as the table or view column type.</span></span> <span data-ttu-id="fc0e1-136">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] `eUserDataType` 引数が BCP_TYPE_SQLDECIMAL または BCP_TYPE_SQLNUMERIC の場合に、ファイル内で一括コピー操作を実行するには、次のようにします。</span><span class="sxs-lookup"><span data-stu-id="fc0e1-136">For bulk copy operations out of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and into a file when the `eUserDataType` argument is BCP_TYPE_SQLDECIMAL or BCP_TYPE_SQLNUMERIC:</span></span>  
  
-   <span data-ttu-id="fc0e1-137">コピー元の列が decimal 型または numeric 型以外の場合は、既定の有効桁数と小数点以下桁数が使用されます。</span><span class="sxs-lookup"><span data-stu-id="fc0e1-137">If the source column is not decimal or numeric, the default precision and scale are used.</span></span>  
  
-   <span data-ttu-id="fc0e1-138">コピー元の列が decimal 型または numeric 型の場合は、コピー元の列の有効桁数と小数点以下桁数が使用されます。</span><span class="sxs-lookup"><span data-stu-id="fc0e1-138">If the source column is decimal or numeric, the precision and scale of the source column are used.</span></span>  
  
 <span data-ttu-id="fc0e1-139">*cbIndicator*[in]</span><span class="sxs-lookup"><span data-stu-id="fc0e1-139">*cbIndicator*[in]</span></span>  
 <span data-ttu-id="fc0e1-140">フィールドのプレフィックス長。</span><span class="sxs-lookup"><span data-stu-id="fc0e1-140">Prefix length for the field.</span></span> <span data-ttu-id="fc0e1-141">既定値は BCP_PREFIX_DEFAULT です。</span><span class="sxs-lookup"><span data-stu-id="fc0e1-141">The default is BCP_PREFIX_DEFAULT.</span></span> <span data-ttu-id="fc0e1-142">有効なプレフィックス長は、0、1、2、4、および 8 です。</span><span class="sxs-lookup"><span data-stu-id="fc0e1-142">The valid lengths for the prefix are 0, 1, 2, 4 and 8.</span></span> <span data-ttu-id="fc0e1-143">フィールドがチャンク分割される場合に頻繁に使用されるプレフィックスのサイズは 8 です。</span><span class="sxs-lookup"><span data-stu-id="fc0e1-143">A prefix size of 8 is most commonly used to indicate that the field is chunked.</span></span> <span data-ttu-id="fc0e1-144">チャンク分割は、大きい値になっている列を効率的に一括コピーするために使用します。</span><span class="sxs-lookup"><span data-stu-id="fc0e1-144">This is used for efficiently bulk copying large value type columns.</span></span>  
  
 <span data-ttu-id="fc0e1-145">*cbUserData*[in]</span><span class="sxs-lookup"><span data-stu-id="fc0e1-145">*cbUserData*[in]</span></span>  
 <span data-ttu-id="fc0e1-146">ユーザー ファイル内にあるフィールド データの最大長 (バイト単位)。長さのインジケーターやターミネータの長さは含まれません。</span><span class="sxs-lookup"><span data-stu-id="fc0e1-146">The maximum length, in bytes, of this field's data in the user file, not including the length of any length indicator or terminator.</span></span>  
  
 <span data-ttu-id="fc0e1-147">`cbUserData`を BCP_LENGTH_NULL に設定すると、データファイルのフィールドのすべての値がであるか、NULL に設定される必要があることを示します。</span><span class="sxs-lookup"><span data-stu-id="fc0e1-147">Setting `cbUserData` to BCP_LENGTH_NULL indicates that all values in the data file fields are, or should be set to NULL.</span></span> <span data-ttu-id="fc0e1-148">`cbUserData`を BCP_LENGTH_VARIABLE に設定すると、各フィールドのデータの長さがシステムによって決定されることになります。</span><span class="sxs-lookup"><span data-stu-id="fc0e1-148">Setting `cbUserData` to BCP_LENGTH_VARIABLE indicates that the system should determine the length of data for each field.</span></span> <span data-ttu-id="fc0e1-149">これは、フィールドによっては、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] からコピーされるデータの前に長さのインジケーターや NULL インジケーターを生成したり、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] にコピーするデータにインジケーターが必要になる場合があることを意味します。</span><span class="sxs-lookup"><span data-stu-id="fc0e1-149">For some fields, this could mean that a length/null indicator is generated to precede data on a copy from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], or that the indicator is expected in data copied to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="fc0e1-150">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]文字データ型およびバイナリデータ型の場合、には `cbUserData` BCP_LENGTH_VARIABLE、BCP_LENGTH_NULL、0、または正の値を指定できます。</span><span class="sxs-lookup"><span data-stu-id="fc0e1-150">For [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] character and binary data types, `cbUserData` can be BCP_LENGTH_VARIABLE, BCP_LENGTH_NULL, 0, or some positive value.</span></span> <span data-ttu-id="fc0e1-151">が BCP_LENGTH_VARIABLE の場合、 `cbUserData` システムは長さインジケーター (存在する場合) またはターミネータシーケンスを使用してデータの長さを決定します。</span><span class="sxs-lookup"><span data-stu-id="fc0e1-151">If `cbUserData` is BCP_LENGTH_VARIABLE, the system uses either the length indicator, if present, or a terminator sequence to determine the length of the data.</span></span> <span data-ttu-id="fc0e1-152">長さのインジケーターとターミネータ シーケンスの両方を指定した場合、一括コピーはコピーするデータ量が少なくなる方法を使用します。</span><span class="sxs-lookup"><span data-stu-id="fc0e1-152">If both a length indicator and a terminator sequence are supplied, bulk copy uses the one that results in the least amount of data being copied.</span></span> <span data-ttu-id="fc0e1-153">`cbUserData`が BCP_LENGTH_VARIABLE の場合、データ型は [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 文字型またはバイナリ型です。長さのインジケーターもターミネータシーケンスも指定されていない場合、システムはエラーメッセージを返します。</span><span class="sxs-lookup"><span data-stu-id="fc0e1-153">If `cbUserData` is BCP_LENGTH_VARIABLE, the data type is a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] character or binary type, and if neither a length indicator nor a terminator sequence is specified, the system returns an error message.</span></span>  
  
 <span data-ttu-id="fc0e1-154">`cbUserData`が0または正の値の場合、システムは `cbUserData` 最大データ長としてを使用します。</span><span class="sxs-lookup"><span data-stu-id="fc0e1-154">If `cbUserData` is 0 or a positive value, the system uses `cbUserData` as the maximum data length.</span></span> <span data-ttu-id="fc0e1-155">ただし、正の `cbUserData` 長さのインジケーターまたはターミネータシーケンスが指定されている場合、システムは、コピーされるデータ量が最小になるメソッドを使用してデータ長を決定します。</span><span class="sxs-lookup"><span data-stu-id="fc0e1-155">However, if, in addition to a positive `cbUserData`, a length indicator or terminator sequence is provided, the system determines the data length by using the method that results in the least amount of data being copied.</span></span>  
  
 <span data-ttu-id="fc0e1-156">値は、 `cbUserData` データのバイト数を表します。</span><span class="sxs-lookup"><span data-stu-id="fc0e1-156">The `cbUserData` value represents the count of bytes of data.</span></span> <span data-ttu-id="fc0e1-157">文字データが Unicode ワイド文字で表されている場合、正の `cbUserData` パラメーター値は、各文字のサイズ (バイト単位) を乗算した文字数を表します。</span><span class="sxs-lookup"><span data-stu-id="fc0e1-157">If character data is represented by Unicode wide characters, then a positive `cbUserData` parameter value represents the number of characters multiplied by the size, in bytes, of each character.</span></span>  
  
 <span data-ttu-id="fc0e1-158">*pbUserDataTerm*[size_is][in]</span><span class="sxs-lookup"><span data-stu-id="fc0e1-158">*pbUserDataTerm*[size_is][in]</span></span>  
 <span data-ttu-id="fc0e1-159">フィールドに使用するターミネータ シーケンス。</span><span class="sxs-lookup"><span data-stu-id="fc0e1-159">The terminator sequence to be used for the field.</span></span> <span data-ttu-id="fc0e1-160">このパラメーターは主に文字データ型に対して有効です。これは、他のすべての型は固定長であったり、バイト数を正確に記録するために長さのインジケーターが必要になる (バイナリ データの場合) ためです。</span><span class="sxs-lookup"><span data-stu-id="fc0e1-160">This parameter is useful mainly for character data types because all other types are of fixed length or, in the case of binary data, require an indicator of length to accurately record the number of bytes present.</span></span>  
  
 <span data-ttu-id="fc0e1-161">抽出されるデータが途中で終了されないようにしたり、ユーザー ファイル内のデータが途中で終了していないことを示すには、このパラメーターに NULL を設定します。</span><span class="sxs-lookup"><span data-stu-id="fc0e1-161">To avoid terminating extracted data, or to indicate that data in a user file is not terminated, set this parameter to NULL.</span></span>  
  
 <span data-ttu-id="fc0e1-162">複数の方法 (ターミネータと長さのインジケーター、ターミネータと列の最大長など) を使用してユーザー ファイルの列長を指定すると、一括コピーはコピーするデータの量が最も少なくなる方法を使用します。</span><span class="sxs-lookup"><span data-stu-id="fc0e1-162">If more than one means of specifying a user-file column length is used (such as a terminator and a length indicator, or a terminator and a maximum column length), bulk copy chooses the one that results in the least amount of data being copied.</span></span>  
  
 <span data-ttu-id="fc0e1-163">一括コピー API では、必要に応じて Unicode から MBCS への文字変換が実行されます。</span><span class="sxs-lookup"><span data-stu-id="fc0e1-163">The bulk copy API performs Unicode-to-MBCS character conversion as required.</span></span> <span data-ttu-id="fc0e1-164">このため、ターミネータのバイト文字列とそのバイト文字列の長さの両方を正しく設定するように注意する必要があります。</span><span class="sxs-lookup"><span data-stu-id="fc0e1-164">Care must be taken to ensure that both the terminator byte string and the length of the byte string are set correctly.</span></span>  
  
 <span data-ttu-id="fc0e1-165">*cbUserDataTerm*[in]</span><span class="sxs-lookup"><span data-stu-id="fc0e1-165">*cbUserDataTerm*[in]</span></span>  
 <span data-ttu-id="fc0e1-166">列に使用するターミネータ シーケンスの長さ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="fc0e1-166">The length, in bytes, of the terminator sequence to be used for the column.</span></span> <span data-ttu-id="fc0e1-167">データ内にターミネータが存在しないか不要な場合は、この値を 0 に設定します。</span><span class="sxs-lookup"><span data-stu-id="fc0e1-167">If no terminator is present or desired in the data, set this value to 0.</span></span>  
  
 <span data-ttu-id="fc0e1-168">*idxServerCol*[in]</span><span class="sxs-lookup"><span data-stu-id="fc0e1-168">*idxServerCol*[in]</span></span>  
 <span data-ttu-id="fc0e1-169">データベース テーブル内での列の序数位置。</span><span class="sxs-lookup"><span data-stu-id="fc0e1-169">The ordinal position of the column in the database table.</span></span> <span data-ttu-id="fc0e1-170">最初の列の序数は 1 です。</span><span class="sxs-lookup"><span data-stu-id="fc0e1-170">The first column number is 1.</span></span> <span data-ttu-id="fc0e1-171">列の序数位置は **IColumnsInfo::GetColumnInfo** などのメソッドから報告されます。</span><span class="sxs-lookup"><span data-stu-id="fc0e1-171">The ordinal position of a column is reported by **IColumnsInfo::GetColumnInfo** or similar methods.</span></span> <span data-ttu-id="fc0e1-172">この値が 0 の場合、一括コピーではデータ ファイル内のこのフィールドは無視されます。</span><span class="sxs-lookup"><span data-stu-id="fc0e1-172">If this value is 0, bulk copy ignores the field in the data file.</span></span>  
  
## <a name="return-code-values"></a><span data-ttu-id="fc0e1-173">リターン コードの値</span><span class="sxs-lookup"><span data-stu-id="fc0e1-173">Return Code Values</span></span>  
 <span data-ttu-id="fc0e1-174">S_OK</span><span class="sxs-lookup"><span data-stu-id="fc0e1-174">S_OK</span></span>  
 <span data-ttu-id="fc0e1-175">メソッドが成功しました。</span><span class="sxs-lookup"><span data-stu-id="fc0e1-175">The method succeeded.</span></span>  
  
 <span data-ttu-id="fc0e1-176">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="fc0e1-176">E_FAIL</span></span>  
 <span data-ttu-id="fc0e1-177">プロバイダー固有のエラーが発生しました。詳細については、 [ISQLServerErrorInfo](../../database-engine/dev-guide/isqlservererrorinfo-ole-db.md)インターフェイスを使用してください。</span><span class="sxs-lookup"><span data-stu-id="fc0e1-177">A provider specific error occurred, for detailed information use the [ISQLServerErrorInfo](../../database-engine/dev-guide/isqlservererrorinfo-ole-db.md) interface.</span></span>  
  
 <span data-ttu-id="fc0e1-178">E_UNEXPECTED</span><span class="sxs-lookup"><span data-stu-id="fc0e1-178">E_UNEXPECTED</span></span>  
 <span data-ttu-id="fc0e1-179">メソッドの呼び出しが予期されませんでした。</span><span class="sxs-lookup"><span data-stu-id="fc0e1-179">The call to the method was unexpected.</span></span> <span data-ttu-id="fc0e1-180">たとえば、このメソッドが呼び出される前に、[IBCPSession::BCPInit](ibcpsession-bcpinit-ole-db.md) メソッドが呼び出されなかった場合などです。</span><span class="sxs-lookup"><span data-stu-id="fc0e1-180">For example, the [IBCPSession::BCPInit](ibcpsession-bcpinit-ole-db.md) method was not called before calling this method.</span></span>  
  
 <span data-ttu-id="fc0e1-181">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="fc0e1-181">E_INVALIDARG</span></span>  
 <span data-ttu-id="fc0e1-182">引数が無効です。</span><span class="sxs-lookup"><span data-stu-id="fc0e1-182">The argument was invalid.</span></span>  
  
 <span data-ttu-id="fc0e1-183">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="fc0e1-183">E_OUTOFMEMORY</span></span>  
 <span data-ttu-id="fc0e1-184">メモリ不足エラー。</span><span class="sxs-lookup"><span data-stu-id="fc0e1-184">Out of memory error.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc0e1-185">参照</span><span class="sxs-lookup"><span data-stu-id="fc0e1-185">See Also</span></span>  
 <span data-ttu-id="fc0e1-186">[IBCPSession &#40;OLE DB&#41;](ibcpsession-ole-db.md) </span><span class="sxs-lookup"><span data-stu-id="fc0e1-186">[IBCPSession &#40;OLE DB&#41;](ibcpsession-ole-db.md) </span></span>  
 [<span data-ttu-id="fc0e1-187">一括コピー操作の実行</span><span class="sxs-lookup"><span data-stu-id="fc0e1-187">Performing Bulk Copy Operations</span></span>](../native-client/features/performing-bulk-copy-operations.md)  
  
  
