---
title: ストアド プロシージャの呼び出し (OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- calling stored procedures
- RPC escape sequence
- OLE DB, stored procedures
- parameters [SQL Server Native Client], OLE DB
- ODBC CALL escape sequence
- stored procedures [OLE DB], calling
- SQL Server Native Client OLE DB provider, stored procedures
ms.assetid: 8e5738e5-4bbe-4f34-bd69-0c0633290bdd
author: rothja
ms.author: jroth
ms.openlocfilehash: 695848c8633d310f5e8ee21e9e738749d1550e4a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738196"
---
# <a name="calling-a-stored-procedure-ole-db"></a><span data-ttu-id="217c3-102">ストアド プロシージャの呼び出し (OLE DB)</span><span class="sxs-lookup"><span data-stu-id="217c3-102">Calling a Stored Procedure (OLE DB)</span></span>
  <span data-ttu-id="217c3-103">ストアド プロシージャは、0 個以上のパラメーターを受け取ることができます。</span><span class="sxs-lookup"><span data-stu-id="217c3-103">A stored procedure can have zero or more parameters.</span></span> <span data-ttu-id="217c3-104">また、値を返すこともできます。</span><span class="sxs-lookup"><span data-stu-id="217c3-104">It can also return a value.</span></span> <span data-ttu-id="217c3-105">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native Client OLE DB プロバイダーを使用する場合、ストアドプロシージャのパラメーターは次の方法で渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="217c3-105">When using the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB provider, parameters to a stored procedure can be passed by:</span></span>  
  
-   <span data-ttu-id="217c3-106">データ値をハードコーディングする。</span><span class="sxs-lookup"><span data-stu-id="217c3-106">Hard-coding the data value.</span></span>  
  
-   <span data-ttu-id="217c3-107">パラメーター マーカー (?) を使用してパラメーターを指定し、プログラム変数をパラメーター マーカーにバインドしてから、データ値をプログラム変数に格納する。</span><span class="sxs-lookup"><span data-stu-id="217c3-107">Using a parameter marker (?) to specify parameters, bind a program variable to the parameter marker, and then place the data value in the program variable.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="217c3-108">OLE DB で名前付きパラメーターを使用して [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ストアド プロシージャを呼び出す場合は、パラメーター名の先頭に '\@' 文字を付ける必要があります。</span><span class="sxs-lookup"><span data-stu-id="217c3-108">When calling [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] stored procedures using named parameters with OLE DB, the parameter names must start with the '\@' character.</span></span> <span data-ttu-id="217c3-109">これは、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 固有の制限です。</span><span class="sxs-lookup"><span data-stu-id="217c3-109">This is a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] specific restriction.</span></span> <span data-ttu-id="217c3-110">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーは、この制限を MDAC よりも厳密に適用します。</span><span class="sxs-lookup"><span data-stu-id="217c3-110">The [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB provider enforces this restriction more strictly than MDAC.</span></span>  
  
 <span data-ttu-id="217c3-111">パラメーターをサポートするには、コマンド オブジェクトで **ICommandWithParameters** インターフェイスを公開します。</span><span class="sxs-lookup"><span data-stu-id="217c3-111">To support parameters, the **ICommandWithParameters** interface is exposed on the command object.</span></span> <span data-ttu-id="217c3-112">パラメーターを使用するには、コンシューマーは、まず、**ICommandWithParameters::SetParameterInfo** メソッドを呼び出して、プロバイダーにパラメーターを示します (または、必要に応じて、**GetParameterInfo** メソッドを呼び出す呼び出し元ステートメントを準備します)。</span><span class="sxs-lookup"><span data-stu-id="217c3-112">To use parameters, the consumer first describes the parameters to the provider by calling the **ICommandWithParameters::SetParameterInfo** method (or optionally prepares a calling statement that calls the **GetParameterInfo** method).</span></span> <span data-ttu-id="217c3-113">次に、バッファーの構造を指定するアクセサーを作成し、このバッファーにパラメーター値を格納します。</span><span class="sxs-lookup"><span data-stu-id="217c3-113">The consumer then creates an accessor that specifies the structure of a buffer and places parameter values in this buffer.</span></span> <span data-ttu-id="217c3-114">最後に、アクセサーのハンドルとバッファーへのポインターを **Execute** に渡します。</span><span class="sxs-lookup"><span data-stu-id="217c3-114">Finally, it passes the handle of the accessor and a pointer to the buffer to **Execute**.</span></span> <span data-ttu-id="217c3-115">その後 **Execute** を呼び出す場合、コンシューマーはバッファーに新しいパラメーター値を格納し、アクセサー ハンドルとバッファー ポインターを指定して **Execute** を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="217c3-115">On later calls to **Execute**, the consumer places new parameter values in the buffer and calls **Execute** with the accessor handle and buffer pointer.</span></span>  
  
 <span data-ttu-id="217c3-116">パラメーターを使用する一時ストアド プロシージャを呼び出すコマンドは、まず、**ICommandWithParameters::SetParameterInfo** を呼び出してパラメーター情報を定義しないと、適切に準備されません。</span><span class="sxs-lookup"><span data-stu-id="217c3-116">A command that calls a temporary stored procedure using parameters must first call **ICommandWithParameters::SetParameterInfo** to define the parameter information, before the command can be successfully prepared.</span></span> <span data-ttu-id="217c3-117">これは、一時ストアド プロシージャの内部名がクライアントで使用される外部名とは異なるので、SQLOLEDB がシステム テーブルをクエリして、一時ストアド プロシージャのパラメーター情報を判断できないためです。</span><span class="sxs-lookup"><span data-stu-id="217c3-117">This is because the internal name for a temporary stored procedure differs from the external name used by a client and SQLOLEDB cannot query the system tables to determine the parameter information for a temporary stored procedure.</span></span>  
  
 <span data-ttu-id="217c3-118">次に、パラメーターのバインド プロセスの手順を示します。</span><span class="sxs-lookup"><span data-stu-id="217c3-118">These are the steps in the parameter binding process:</span></span>  
  
1.  <span data-ttu-id="217c3-119">DBPARAMBINDINFO 構造体の配列にパラメーター情報を格納します。パラメーター情報には、パラメーター名、パラメーターのデータ型を表すプロバイダー固有の名前、標準のデータ型名などが含まれます。</span><span class="sxs-lookup"><span data-stu-id="217c3-119">Fill in the parameter information in an array of DBPARAMBINDINFO structures; that is, parameter name, provider-specific name for the data type of the parameter or a standard data type name, and so on.</span></span> <span data-ttu-id="217c3-120">配列内の構造体 1 つが、1 つのパラメーターを表します。</span><span class="sxs-lookup"><span data-stu-id="217c3-120">Each structure in the array describes one parameter.</span></span> <span data-ttu-id="217c3-121">その後、この配列は **SetParameterInfo** メソッドに渡されます。</span><span class="sxs-lookup"><span data-stu-id="217c3-121">This array is then passed to the **SetParameterInfo** method.</span></span>  
  
2.  <span data-ttu-id="217c3-122">**ICommandWithParameters::SetParameterInfo** メソッドを呼び出して、パラメーターをプロバイダーに示します。</span><span class="sxs-lookup"><span data-stu-id="217c3-122">Call the **ICommandWithParameters::SetParameterInfo** method to describe parameters to the provider.</span></span> <span data-ttu-id="217c3-123">**SetParameterInfo** では、各パラメーターのネイティブ データ型を指定します。</span><span class="sxs-lookup"><span data-stu-id="217c3-123">**SetParameterInfo** specifies the native data type of each parameter.</span></span> <span data-ttu-id="217c3-124">**SetParameterInfo** 引数は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="217c3-124">**SetParameterInfo** arguments are:</span></span>  
  
    -   <span data-ttu-id="217c3-125">型情報を設定するパラメーターの数</span><span class="sxs-lookup"><span data-stu-id="217c3-125">The number of parameters for which to set type information.</span></span>  
  
    -   <span data-ttu-id="217c3-126">型情報を設定するパラメーターの序数の配列</span><span class="sxs-lookup"><span data-stu-id="217c3-126">An array of parameter ordinals for which to set type information.</span></span>  
  
    -   <span data-ttu-id="217c3-127">DBPARAMBINDINFO 構造体の配列</span><span class="sxs-lookup"><span data-stu-id="217c3-127">An array of DBPARAMBINDINFO structures.</span></span>  
  
3.  <span data-ttu-id="217c3-128">**IAccessor::CreateAccessor** コマンドを使用して、パラメーター アクセサーを作成します。</span><span class="sxs-lookup"><span data-stu-id="217c3-128">Create a parameter accessor by using the **IAccessor::CreateAccessor** command.</span></span> <span data-ttu-id="217c3-129">このアクセサーにより、バッファーの構造を指定し、パラメーター値をバッファーに格納します。</span><span class="sxs-lookup"><span data-stu-id="217c3-129">The accessor specifies the structure of a buffer and places parameter values in the buffer.</span></span> <span data-ttu-id="217c3-130">**CreateAccessor** コマンドでは、バインドのセットからアクセサーを作成します。</span><span class="sxs-lookup"><span data-stu-id="217c3-130">The **CreateAccessor** command creates an accessor from a set of bindings.</span></span> <span data-ttu-id="217c3-131">このバインドは、コンシューマーが DBBINDING 構造体の配列を使用して記述します。</span><span class="sxs-lookup"><span data-stu-id="217c3-131">These bindings are described by the consumer by using an array of DBBINDING structures.</span></span> <span data-ttu-id="217c3-132">各バインドでは、1 つのパラメーターをコンシューマーのバッファーに関連付けます。バインドには、次のような情報が含まれます。</span><span class="sxs-lookup"><span data-stu-id="217c3-132">Each binding associates a single parameter to the buffer of the consumer and contains information such as:</span></span>  
  
    -   <span data-ttu-id="217c3-133">バインドが適用されるパラメーターの序数</span><span class="sxs-lookup"><span data-stu-id="217c3-133">The ordinal of the parameter to which the binding applies.</span></span>  
  
    -   <span data-ttu-id="217c3-134">バインドの対象 (データ値、データ値の長さと状態)</span><span class="sxs-lookup"><span data-stu-id="217c3-134">What is bound (the data value, its length, and its status).</span></span>  
  
    -   <span data-ttu-id="217c3-135">これらの各情報に関するバッファー内のオフセット</span><span class="sxs-lookup"><span data-stu-id="217c3-135">The offset in the buffer to each of these parts.</span></span>  
  
    -   <span data-ttu-id="217c3-136">コンシューマーのバッファー内にあるデータ値の長さと型</span><span class="sxs-lookup"><span data-stu-id="217c3-136">The length and type of the data value as it exists in the buffer of the consumer.</span></span>  
  
     <span data-ttu-id="217c3-137">アクセサーは、アクセサーのハンドルにより識別されます。このハンドルは HACCESSOR 型です。</span><span class="sxs-lookup"><span data-stu-id="217c3-137">An accessor is identified by its handle, which is of type HACCESSOR.</span></span> <span data-ttu-id="217c3-138">このハンドルは、**CreateAccessor** メソッドから返されます。</span><span class="sxs-lookup"><span data-stu-id="217c3-138">This handle is returned by the **CreateAccessor** method.</span></span> <span data-ttu-id="217c3-139">コンシューマーはアクセサーを使い終わるたびに、**ReleaseAccessor** メソッドを呼び出して、アクセサーが保持しているメモリを解放する必要があります。</span><span class="sxs-lookup"><span data-stu-id="217c3-139">Whenever the consumer finishes using an accessor, the consumer must call the **ReleaseAccessor** method to release the memory it holds.</span></span>  
  
     <span data-ttu-id="217c3-140">コンシューマーが **ICommand::Execute** などのメソッドを呼び出す場合、アクセサーへのハンドルとバッファー自体へのポインターを渡します。</span><span class="sxs-lookup"><span data-stu-id="217c3-140">When the consumer calls a method, such as **ICommand::Execute**, it passes the handle to an accessor and a pointer to a buffer itself.</span></span> <span data-ttu-id="217c3-141">プロバイダーはこのアクセサーを使用して、バッファー内にあるデータを送信する方法を決定します。</span><span class="sxs-lookup"><span data-stu-id="217c3-141">The provider uses this accessor to determine how to transfer the data contained in the buffer.</span></span>  
  
4.  <span data-ttu-id="217c3-142">DBPARAMS 構造体にデータを格納します。</span><span class="sxs-lookup"><span data-stu-id="217c3-142">Fill in the DBPARAMS structure.</span></span> <span data-ttu-id="217c3-143">入力パラメーター値の取得と出力パラメーター値の書き込みに使われるコンシューマーの変数が、実行時に DBPARAMS 構造体の **ICommand::Execute** に渡されます。</span><span class="sxs-lookup"><span data-stu-id="217c3-143">The consumer variables from which input parameter values are taken and to which output parameter values are written are passed at run time to **ICommand::Execute** in the DBPARAMS structure.</span></span> <span data-ttu-id="217c3-144">DBPARAMS 構造体には、次の 3 つの要素が含まれます。</span><span class="sxs-lookup"><span data-stu-id="217c3-144">The DBPARAMS structure includes three elements:</span></span>  
  
    -   <span data-ttu-id="217c3-145">アクセサー ハンドルで指定されているバインドに従ってプロバイダーが入力パラメーター データを取得し、出力パラメーター データを返すための、バッファーへのポインター</span><span class="sxs-lookup"><span data-stu-id="217c3-145">A pointer to the buffer from which the provider retrieves input parameter data and to which the provider returns output parameter data, according to the bindings specified by the accessor handle.</span></span>  
  
    -   <span data-ttu-id="217c3-146">バッファー内のパラメーター セットの数</span><span class="sxs-lookup"><span data-stu-id="217c3-146">The number of sets of parameters in the buffer.</span></span>  
  
    -   <span data-ttu-id="217c3-147">手順 3. で作成したアクセサー ハンドル</span><span class="sxs-lookup"><span data-stu-id="217c3-147">The accessor handle created in Step 3.</span></span>  
  
5.  <span data-ttu-id="217c3-148">**ICommand::Execute** を使用してコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="217c3-148">Execute the command by using **ICommand::Execute**.</span></span>  
  
## <a name="methods-of-calling-a-stored-procedure"></a><span data-ttu-id="217c3-149">ストアド プロシージャを呼び出す方法</span><span class="sxs-lookup"><span data-stu-id="217c3-149">Methods of Calling a Stored Procedure</span></span>  
 <span data-ttu-id="217c3-150">でストアドプロシージャを実行すると、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーは次の機能をサポートします。</span><span class="sxs-lookup"><span data-stu-id="217c3-150">When executing a stored procedure in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB provider supports the:</span></span>  
  
-   <span data-ttu-id="217c3-151">ODBC CALL エスケープ シーケンス。</span><span class="sxs-lookup"><span data-stu-id="217c3-151">ODBC CALL escape sequence.</span></span>  
  
-   <span data-ttu-id="217c3-152">リモート プロシージャ コール (RPC) エスケープ シーケンス</span><span class="sxs-lookup"><span data-stu-id="217c3-152">Remote procedure call (RPC) escape sequence.</span></span>  
  
-   [!INCLUDE[tsql](../../../includes/tsql-md.md)] <span data-ttu-id="217c3-153">EXECUTE ステートメント</span><span class="sxs-lookup"><span data-stu-id="217c3-153">EXECUTE statement.</span></span>  
  
### <a name="odbc-call-escape-sequence"></a><span data-ttu-id="217c3-154">ODBC CALL エスケープ シーケンス</span><span class="sxs-lookup"><span data-stu-id="217c3-154">ODBC CALL Escape Sequence</span></span>  
 <span data-ttu-id="217c3-155">パラメーター情報を把握している場合は、**ICommandWithParameters::SetParameterInfo** メソッドを呼び出して、パラメーターをプロバイダーに示します。</span><span class="sxs-lookup"><span data-stu-id="217c3-155">If you know parameter information, call **ICommandWithParameters::SetParameterInfo** method to describe the parameters to the provider.</span></span> <span data-ttu-id="217c3-156">それ以外の場合は、ストアド プロシージャの呼び出しに ODBC CALL 構文を使用すると、プロバイダーはヘルパー関数を呼び出してストアド プロシージャのパラメーター情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="217c3-156">Otherwise, when the ODBC CALL syntax is used in calling a stored procedure, the provider calls a helper function to find the stored procedure parameter information.</span></span>  
  
 <span data-ttu-id="217c3-157">パラメーター情報 (パラメーターのメタデータ) を把握していない場合は、ODBC CALL 構文の使用をお勧めします。</span><span class="sxs-lookup"><span data-stu-id="217c3-157">If you are not sure about the parameter information (parameter metadata), ODBC CALL syntax is recommended.</span></span>  
  
 <span data-ttu-id="217c3-158">ODBC CALL エスケープ シーケンスを使用してプロシージャを呼び出す場合の一般的な構文は、次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="217c3-158">The general syntax for calling a procedure by using the ODBC CALL escape sequence is:</span></span>  
  
 <span data-ttu-id="217c3-159">{[**? =**]**呼び出し**_procedure_name_[**(**[*parameter*] [**,**[*parameter*]]...**)**]}</span><span class="sxs-lookup"><span data-stu-id="217c3-159">{[**?=**]**call**_procedure_name_[**(**[*parameter*][**,**[*parameter*]]...**)**]}</span></span>  
  
 <span data-ttu-id="217c3-160">例:</span><span class="sxs-lookup"><span data-stu-id="217c3-160">For example:</span></span>  
  
```  
{call SalesByCategory('Produce', '1995')}  
```  
  
### <a name="rpc-escape-sequence"></a><span data-ttu-id="217c3-161">RPC エスケープ シーケンス</span><span class="sxs-lookup"><span data-stu-id="217c3-161">RPC Escape Sequence</span></span>  
 <span data-ttu-id="217c3-162">RPC エスケープ シーケンスは、ストアド プロシージャを呼び出す ODBC CALL 構文と似ています。</span><span class="sxs-lookup"><span data-stu-id="217c3-162">The RPC escape sequence is similar to the ODBC CALL syntax of calling a stored procedure.</span></span> <span data-ttu-id="217c3-163">プロシージャを複数回呼び出す場合は、ストアド プロシージャを呼び出す 3 つの方法のうち、RPC エスケープ シーケンスのパフォーマンスが最も優れています。</span><span class="sxs-lookup"><span data-stu-id="217c3-163">If you will call the procedure multiple times, the RPC escape sequence provides most optimal performance among the three methods of calling a stored procedure.</span></span>  
  
 <span data-ttu-id="217c3-164">RPC エスケープ シーケンスを使用してストアド プロシージャを実行する場合、プロバイダーはパラメーター情報の決定にヘルパー関数を呼び出しません (ODBC CALL 構文では、ヘルパー関数が呼び出されます)。</span><span class="sxs-lookup"><span data-stu-id="217c3-164">When the RPC escape sequence is used to execute a stored procedure, the provider does not call any helper function to determine the parameter information (as it does in the case of ODBC CALL syntax).</span></span> <span data-ttu-id="217c3-165">RPC 構文は ODBC CALL 構文よりも簡単です。そのためコマンドが高速に解析され、パフォーマンスが向上します。</span><span class="sxs-lookup"><span data-stu-id="217c3-165">The RPC syntax is simpler than the ODBC CALL syntax, so the command is parsed faster, improving performance.</span></span> <span data-ttu-id="217c3-166">この場合は、**ICommandWithParameters::SetParameterInfo** を実行してパラメーター情報を提供する必要があります。</span><span class="sxs-lookup"><span data-stu-id="217c3-166">In this case, you need to provide the parameter information by executing **ICommandWithParameters::SetParameterInfo**.</span></span>  
  
 <span data-ttu-id="217c3-167">RPC エスケープ シーケンスを使用する場合は、戻り値が必要です。</span><span class="sxs-lookup"><span data-stu-id="217c3-167">The RPC escape sequence requires you to have a return value.</span></span> <span data-ttu-id="217c3-168">ストアド プロシージャが値を返さない場合、サーバーが既定で 0 を返します。</span><span class="sxs-lookup"><span data-stu-id="217c3-168">If the stored procedure does not return a value, the server returns a 0 by default.</span></span> <span data-ttu-id="217c3-169">また、ストアド プロシージャ上で [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] カーソルを開くことはできません。</span><span class="sxs-lookup"><span data-stu-id="217c3-169">In addition, you cannot open a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] cursor on the stored procedure.</span></span> <span data-ttu-id="217c3-170">ストアド プロシージャは暗黙的に準備され、**ICommandPrepare::Prepare** の呼び出しは失敗します。</span><span class="sxs-lookup"><span data-stu-id="217c3-170">The stored procedure is prepared implicitly and the call to **ICommandPrepare::Prepare** will fail.</span></span> <span data-ttu-id="217c3-171">RPC 呼び出しを準備できないため、列のメタデータをクエリすることはできません。IColumnsInfo::GetColumnInfo と IColumnsRowset::GetColumnsRowset によって DB_E_NOTPREPARED が返されます。</span><span class="sxs-lookup"><span data-stu-id="217c3-171">Because of the inability to prepare an RPC call, you can not query column metadata; IColumnsInfo::GetColumnInfo and IColumnsRowset::GetColumnsRowset will return DB_E_NOTPREPARED.</span></span>  
  
 <span data-ttu-id="217c3-172">パラメーターのメタデータを把握できている場合は、ストアド プロシージャの実行方法として RPC エスケープ シーケンスの使用をお勧めします。</span><span class="sxs-lookup"><span data-stu-id="217c3-172">If you know all the parameter metadata, RPC escape sequence is the recommended way to execute stored procedures.</span></span>  
  
 <span data-ttu-id="217c3-173">次に、ストアド プロシージャを呼び出す RPC エスケープ シーケンスの例を示します。</span><span class="sxs-lookup"><span data-stu-id="217c3-173">This is an example of RPC escape sequence for calling a stored procedure:</span></span>  
  
```  
{rpc SalesByCategory}  
```  
  
 <span data-ttu-id="217c3-174">RPC エスケープ シーケンスを示すサンプル アプリケーションについては、[ストアド プロシージャの実行 &#40;RPC 構文を使用&#41; とリターン コードおよび出力パラメーターの処理 &#40;OLE DB&#41;](../../native-client-ole-db-how-to/results/execute-stored-procedure-with-rpc-and-process-output.md) に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="217c3-174">For a sample application that demonstrates an RPC escape sequence, see [Execute a Stored Procedure &#40;Using RPC Syntax&#41; and Process Return Codes and Output Parameters &#40;OLE DB&#41;](../../native-client-ole-db-how-to/results/execute-stored-procedure-with-rpc-and-process-output.md).</span></span>  
  
### <a name="transact-sql-execute-statement"></a><span data-ttu-id="217c3-175">Transact-SQL EXECUTE ステートメント</span><span class="sxs-lookup"><span data-stu-id="217c3-175">Transact-SQL EXECUTE Statement</span></span>  
 <span data-ttu-id="217c3-176">ストアド プロシージャを呼び出す方法としては、[EXECUTE](/sql/t-sql/language-elements/execute-transact-sql) ステートメントよりも、ODBC CALL エスケープ シーケンスや RPC エスケープ シーケンスをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="217c3-176">The ODBC CALL escape sequence and the RPC escape sequence are the preferred methods for calling a stored procedure rather than the [EXECUTE](/sql/t-sql/language-elements/execute-transact-sql) statement.</span></span> <span data-ttu-id="217c3-177">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native Client OLE DB プロバイダーは、の RPC 機構を使用して [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] コマンド処理を最適化します。</span><span class="sxs-lookup"><span data-stu-id="217c3-177">The [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB provider uses the RPC mechanism of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] to optimize command processing.</span></span> <span data-ttu-id="217c3-178">この RPC プロトコルでは、サーバー側で実行されるパラメーター処理やステートメントの解析作業の多くを排除することで、パフォーマンスを向上しています。</span><span class="sxs-lookup"><span data-stu-id="217c3-178">This RPC protocol increases performance by eliminating much of the parameter processing and statement parsing done on the server.</span></span>  
  
 <span data-ttu-id="217c3-179">[!INCLUDE[tsql](../../../includes/tsql-md.md)] **EXECUTE** ステートメントの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="217c3-179">This is an example of the [!INCLUDE[tsql](../../../includes/tsql-md.md)] **EXECUTE** statement:</span></span>  
  
```  
EXECUTE SalesByCategory 'Produce', '1995'  
```  
  
## <a name="see-also"></a><span data-ttu-id="217c3-180">参照</span><span class="sxs-lookup"><span data-stu-id="217c3-180">See Also</span></span>  
 [<span data-ttu-id="217c3-181">ストアド プロシージャ</span><span class="sxs-lookup"><span data-stu-id="217c3-181">Stored Procedures</span></span>](stored-procedures.md)  
  
  
