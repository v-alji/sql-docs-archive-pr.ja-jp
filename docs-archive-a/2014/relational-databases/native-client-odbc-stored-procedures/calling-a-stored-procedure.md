---
title: ストアドプロシージャを呼び出す |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- calling stored procedures
- ODBC, stored procedures
- stored procedures [ODBC], calling
- SQL Server Native Client ODBC driver, stored procedures
- ODBC CALL escape sequence
- escape sequences [SQL Server]
- CALL statement
ms.assetid: d13737f4-f641-45bf-b56c-523e2ffc080f
author: rothja
ms.author: jroth
ms.openlocfilehash: c6fa704e45e4e85b479ae8a40a3e567bea1ec5e9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741958"
---
# <a name="calling-a-stored-procedure"></a><span data-ttu-id="e5c01-102">ストアド プロシージャの呼び出し</span><span class="sxs-lookup"><span data-stu-id="e5c01-102">Calling a Stored Procedure</span></span>
  <span data-ttu-id="e5c01-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native CLIENT odbc ドライバーでは、ストアドプロシージャを実行するための ODBC call エスケープシーケンスと EXECUTE ステートメントの両方がサポートされています [!INCLUDE[tsql](../../includes/tsql-md.md)] [EXECUTE](/sql/t-sql/language-elements/execute-transact-sql) 。 odbc call エスケープシーケンスを使用する方法をお勧めします。</span><span class="sxs-lookup"><span data-stu-id="e5c01-103">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver supports both the ODBC CALL escape sequence and the [!INCLUDE[tsql](../../includes/tsql-md.md)][EXECUTE](/sql/t-sql/language-elements/execute-transact-sql) statement for executing stored procedures; the ODBC CALL escape sequence is the preferred method.</span></span> <span data-ttu-id="e5c01-104">ODBC 構文を使用すると、アプリケーションでストアド プロシージャのリターン コードを取得できます。また、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を実行するコンピューター間のリモート プロシージャ コール (RPC) の送信向けに開発されているプロトコルを使用するように最適化されます。</span><span class="sxs-lookup"><span data-stu-id="e5c01-104">Using ODBC syntax enables an application to retrieve the return codes of stored procedures and the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver is also optimized to use a protocol originally developed for sending remote procedure (RPC) calls between computers running [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="e5c01-105">この RPC プロトコルでは、サーバー側で実行されるパラメーター処理やステートメントの解析作業の多くを排除することで、パフォーマンスを向上しています。</span><span class="sxs-lookup"><span data-stu-id="e5c01-105">This RPC protocol increases performance by eliminating much of the parameter processing and statement parsing done on the server.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e5c01-106">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ODBC で名前付きパラメーターを使用してストアドプロシージャを呼び出す場合 (詳細については、「[名前によるパラメーターのバインド (名前付きパラメーター)](https://go.microsoft.com/fwlink/?LinkID=209721)」を参照)、パラメーター名は ' ' 文字で始める必要があり \@ ます。</span><span class="sxs-lookup"><span data-stu-id="e5c01-106">When calling [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] stored procedures using named parameters with ODBC (for more information, see [Binding Parameters by Name (Named Parameters)](https://go.microsoft.com/fwlink/?LinkID=209721)), the parameter names must start with the '\@' character.</span></span> <span data-ttu-id="e5c01-107">これは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 固有の制限です。</span><span class="sxs-lookup"><span data-stu-id="e5c01-107">This is a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] specific restriction.</span></span> <span data-ttu-id="e5c01-108">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーでは、Microsoft Data Access Components (MDAC) の場合よりも厳密にこの制限が適用されます。</span><span class="sxs-lookup"><span data-stu-id="e5c01-108">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver enforces this restriction more strictly than the Microsoft Data Access Components (MDAC).</span></span>  
  
 <span data-ttu-id="e5c01-109">プロシージャを呼び出す ODBC CALL エスケープ シーケンスは、次の構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="e5c01-109">The ODBC CALL escape sequence for calling a procedure is:</span></span>  
  
 <span data-ttu-id="e5c01-110">{[**? =**]**呼び出し**_procedure_name_[([*parameter*] [**,**[*parameter*]]...)]}</span><span class="sxs-lookup"><span data-stu-id="e5c01-110">{[**?=**]**call**_procedure_name_[([*parameter*][**,**[*parameter*]]...)]}</span></span>  
  
 <span data-ttu-id="e5c01-111">ここで*procedure_name*プロシージャの名前を指定し、*パラメーター*はプロシージャパラメーターを指定します。</span><span class="sxs-lookup"><span data-stu-id="e5c01-111">where *procedure_name* specifies the name of a procedure and *parameter* specifies a procedure parameter.</span></span> <span data-ttu-id="e5c01-112">名前付きパラメーターは、ODBC CALL エスケープ シーケンスを使用するステートメントでのみサポートされます。</span><span class="sxs-lookup"><span data-stu-id="e5c01-112">Named parameters are only supported in statements using the ODBC CALL escape sequence.</span></span>  
  
 <span data-ttu-id="e5c01-113">プロシージャには、0 個以上のパラメーターを指定できます。</span><span class="sxs-lookup"><span data-stu-id="e5c01-113">A procedure can have zero or more parameters.</span></span> <span data-ttu-id="e5c01-114">また、構文の先頭に省略可能なパラメーター マーカー ?= を指定することによって値を返すこともできます。</span><span class="sxs-lookup"><span data-stu-id="e5c01-114">It can also return a value (as indicated by the optional parameter marker ?= at the start of the syntax).</span></span> <span data-ttu-id="e5c01-115">パラメーターが入力パラメーターまたは入出力パラメーターの場合は、リテラルまたはパラメーター マーカーを使用できます。</span><span class="sxs-lookup"><span data-stu-id="e5c01-115">If a parameter is an input or an input/output parameter, it can be a literal or a parameter marker.</span></span> <span data-ttu-id="e5c01-116">パラメーターが出力パラメーターの場合、出力は不明なので、パラメーター マーカーを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e5c01-116">If the parameter is an output parameter, it must be a parameter marker because the output is unknown.</span></span> <span data-ttu-id="e5c01-117">プロシージャ呼び出しステートメントを実行する前に、パラメーターマーカーを[SQLBindParameter](../../relational-databases/native-client-odbc-api/sqlbindparameter.md)にバインドする必要があります。</span><span class="sxs-lookup"><span data-stu-id="e5c01-117">Parameter markers must be bound with [SQLBindParameter](../../relational-databases/native-client-odbc-api/sqlbindparameter.md) before the procedure call statement is executed.</span></span>  
  
 <span data-ttu-id="e5c01-118">プロシージャ呼び出しでは、入力パラメーターと入出力パラメーターを省略できます。</span><span class="sxs-lookup"><span data-stu-id="e5c01-118">Input and input/output parameters can be omitted from procedure calls.</span></span> <span data-ttu-id="e5c01-119">かっこだけを指定し、パラメーターを指定しないでプロシージャを呼び出した場合、ドライバーは最初のパラメーターの既定値を使用するように、データ ソースに指示します。</span><span class="sxs-lookup"><span data-stu-id="e5c01-119">If a procedure is called with parentheses but without any parameters, the driver instructs the data source to use the default value for the first parameter.</span></span> <span data-ttu-id="e5c01-120">例:</span><span class="sxs-lookup"><span data-stu-id="e5c01-120">For example:</span></span>  
  
 <span data-ttu-id="e5c01-121">{**call** _procedure_name_**()**} を呼び出します</span><span class="sxs-lookup"><span data-stu-id="e5c01-121">{**call** _procedure_name_**( )**}</span></span>  
  
 <span data-ttu-id="e5c01-122">プロシージャにパラメーターを指定しないと、失敗する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="e5c01-122">If the procedure does not have any parameters, the procedure can fail.</span></span> <span data-ttu-id="e5c01-123">かっこを付けないでプロシージャを呼び出すと、ドライバーはパラメーター値を送信しません。</span><span class="sxs-lookup"><span data-stu-id="e5c01-123">If a procedure is called without parentheses, the driver does not send any parameter values.</span></span> <span data-ttu-id="e5c01-124">例:</span><span class="sxs-lookup"><span data-stu-id="e5c01-124">For example:</span></span>  
  
 <span data-ttu-id="e5c01-125">{**call** _procedure_name_} を呼び出します</span><span class="sxs-lookup"><span data-stu-id="e5c01-125">{**call** _procedure_name_}</span></span>  
  
 <span data-ttu-id="e5c01-126">プロシージャ呼び出しでは、入力パラメーターや入出力パラメーターとしてリテラルを指定できます。</span><span class="sxs-lookup"><span data-stu-id="e5c01-126">Literals can be specified for input and input/output parameters in procedure calls.</span></span> <span data-ttu-id="e5c01-127">たとえば、InsertOrder プロシージャには 5 つの入力パラメーターがあるとします。</span><span class="sxs-lookup"><span data-stu-id="e5c01-127">For example, the procedure InsertOrder has five input parameters.</span></span> <span data-ttu-id="e5c01-128">次の InsertOrder の呼び出しでは、最初のパラメーターを省略し、2 番目のパラメーターとしてリテラルを指定して、3 番目、4 番目、5 番目のパラメーターとしてパラメーター マーカーを使用しています</span><span class="sxs-lookup"><span data-stu-id="e5c01-128">The following call to InsertOrder omits the first parameter, provides a literal for the second parameter, and uses a parameter marker for the third, fourth, and fifth parameters.</span></span> <span data-ttu-id="e5c01-129">(パラメーターには、値 1 から始まる序数が付けられます)。</span><span class="sxs-lookup"><span data-stu-id="e5c01-129">(Parameters are numbered sequentially, beginning with a value of 1.)</span></span>  
  
```  
{call InsertOrder(, 10, ?, ?, ?)}  
```  
  
 <span data-ttu-id="e5c01-130">パラメーターを省略する場合でも、他のパラメーターとの区切りを示すコンマは省略できないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="e5c01-130">Note that if a parameter is omitted, the comma delimiting it from other parameters must still appear.</span></span> <span data-ttu-id="e5c01-131">入力パラメーターまたは入出力パラメーターを省略すると、プロシージャはそのパラメーターの既定値を使用します。</span><span class="sxs-lookup"><span data-stu-id="e5c01-131">If an input or input/output parameter is omitted, the procedure uses the default value of the parameter.</span></span> <span data-ttu-id="e5c01-132">他の方法で入力パラメーターまたは入出力パラメーターの既定値を指定するには、そのパラメーターにバインドされる長さ/インジケーター バッファーの値を SQL_DEFAULT_PARAM に設定するか、DEFAULT キーワードを使用します。</span><span class="sxs-lookup"><span data-stu-id="e5c01-132">Other ways to specify the default value of an input or input/output parameter are to set the value of the length/indicator buffer bound to the parameter to SQL_DEFAULT_PARAM, or to use the DEFAULT keyword.</span></span>  
  
 <span data-ttu-id="e5c01-133">入出力パラメーターを省略した場合、または入出力パラメーターとしてリテラルを指定した場合、ドライバーは出力値を破棄します。</span><span class="sxs-lookup"><span data-stu-id="e5c01-133">If an input/output parameter is omitted, or if a literal is supplied for the parameter, the driver discards the output value.</span></span> <span data-ttu-id="e5c01-134">同様に、プロシージャの戻り値のパラメーター マーカーを省略した場合、ドライバーは戻り値を破棄します。</span><span class="sxs-lookup"><span data-stu-id="e5c01-134">Similarly, if the parameter marker for the return value of a procedure is omitted, the driver discards the return value.</span></span> <span data-ttu-id="e5c01-135">最後に、値を返さないプロシージャに戻り値パラメーターを指定すると、ドライバーは、そのパラメーターにバインドされる長さ/インジケーター バッファーの値を SQL_NULL_DATA に設定します。</span><span class="sxs-lookup"><span data-stu-id="e5c01-135">Finally, if an application specifies a return value parameter for a procedure that does not return a value, the driver sets the value of the length/indicator buffer bound to the parameter to SQL_NULL_DATA.</span></span>  
  
## <a name="delimiters-in-call-statements"></a><span data-ttu-id="e5c01-136">CALL ステートメント内の区切り記号</span><span class="sxs-lookup"><span data-stu-id="e5c01-136">Delimiters in CALL Statements</span></span>  
 <span data-ttu-id="e5c01-137">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native CLIENT odbc ドライバーは、既定で odbc {CALL} エスケープシーケンスに固有の互換性オプションもサポートしています。</span><span class="sxs-lookup"><span data-stu-id="e5c01-137">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver by default also supports a compatibility option specific to the ODBC { CALL } escape sequence.</span></span> <span data-ttu-id="e5c01-138">ドライバーは、1 組の二重引用符でストアド プロシージャ名全体を区切る CALL ステートメントを受け付けます。</span><span class="sxs-lookup"><span data-stu-id="e5c01-138">The driver accepts CALL statements with only a single set of double quotation marks delimiting the entire stored procedure name:</span></span>  
  
```  
{ CALL "master.dbo.sp_who" }  
```  
  
 <span data-ttu-id="e5c01-139">また既定では、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーは、ISO の規則に従い、各識別子を二重引用符で囲んだ CALL ステートメントも受け付けます。</span><span class="sxs-lookup"><span data-stu-id="e5c01-139">By default the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver also accepts CALL statements that follow the ISO rules and enclose each identifier in double quotation marks:</span></span>  
  
```  
{ CALL "master"."dbo"."sp_who" }  
```  
  
 <span data-ttu-id="e5c01-140">ただし、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーを既定の設定で実行している場合、ISO 標準では無効とされている文字を含む識別子については、どちらの形式の引用符の使用もサポートされません。</span><span class="sxs-lookup"><span data-stu-id="e5c01-140">When running with the default settings, however, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver does not support using either form of quoted identifier with identifiers that contain characters not specified as legal in identifiers by the ISO standard.</span></span> <span data-ttu-id="e5c01-141">たとえば、ドライバーは、引用符で囲まれた識別子を含む CALL ステートメントを使用して、 **"My. Proc"** という名前のストアドプロシージャにアクセスすることはできません。</span><span class="sxs-lookup"><span data-stu-id="e5c01-141">For example, the driver cannot access a stored procedure named **"My.Proc"** using a CALL statement with quoted identifiers:</span></span>  
  
```  
{ CALL "MyDB"."MyOwner"."My.Proc" }  
```  
  
 <span data-ttu-id="e5c01-142">このステートメントは、ドライバーでは次のように解釈されます。</span><span class="sxs-lookup"><span data-stu-id="e5c01-142">This statement is interpreted by the driver as:</span></span>  
  
```  
{ CALL MyDB.MyOwner.My.Proc }  
```  
  
 <span data-ttu-id="e5c01-143">サーバーでは、 **MyDB**という名前のリンクサーバーが存在しないというエラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="e5c01-143">The server raises an error that a linked server named **MyDB** does not exist.</span></span>  
  
 <span data-ttu-id="e5c01-144">この問題は、角かっこで囲まれる識別子を使用すると発生しません。つまり、次のステートメントは正しく解釈されます。</span><span class="sxs-lookup"><span data-stu-id="e5c01-144">The issue does not exist when using bracketed identifiers, this statement is interpreted correctly:</span></span>  
  
```  
{ CALL [MyDB].[MyOwner].[My.Table] }  
```  
  
## <a name="see-also"></a><span data-ttu-id="e5c01-145">参照</span><span class="sxs-lookup"><span data-stu-id="e5c01-145">See Also</span></span>  
 [<span data-ttu-id="e5c01-146">ストアド プロシージャの実行</span><span class="sxs-lookup"><span data-stu-id="e5c01-146">Running Stored Procedures</span></span>](../../relational-databases/native-client-odbc-stored-procedures/running-stored-procedures.md)  
  
  
