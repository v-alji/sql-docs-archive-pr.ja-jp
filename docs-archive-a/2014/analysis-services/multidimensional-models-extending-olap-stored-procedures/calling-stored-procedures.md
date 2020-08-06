---
title: ストアドプロシージャの呼び出し |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- calling stored procedures
- stored procedures [Analysis Services], calling
- MDX queries [Analysis Services]
- CALL statement
ms.assetid: 96a9660d-875b-4ee4-b339-90020b1d9895
author: minewiskan
ms.author: owend
ms.openlocfilehash: 5c9da6edef576a6ab25c183cbc87ff95cc056845
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87715849"
---
# <a name="calling-stored-procedures"></a><span data-ttu-id="65fd4-102">ストアド プロシージャを呼び出す</span><span class="sxs-lookup"><span data-stu-id="65fd4-102">Calling Stored Procedures</span></span>
  <span data-ttu-id="65fd4-103">ストアド プロシージャは、サーバーまたはクライアント アプリケーションから呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="65fd4-103">Stored procedures can be called on the server or from client application.</span></span> <span data-ttu-id="65fd4-104">どちらの場合も、ストアド プロシージャはサーバーまたはデータベースのコンテキストで常にサーバー上で実行します。</span><span class="sxs-lookup"><span data-stu-id="65fd4-104">In either case, stored procedures always run on the server, either the context of the server or of a database.</span></span> <span data-ttu-id="65fd4-105">ストアド プロシージャを実行するのに特別なアクセス権は不要です。</span><span class="sxs-lookup"><span data-stu-id="65fd4-105">There are no special permissions required to execute a stored procedure.</span></span> <span data-ttu-id="65fd4-106">ストアド プロシージャがアセンブリによってサーバーまたはデータベースのコンテキストに追加されると、ストアド プロシージャが行う処理がユーザーのロールで許可されている限り、どのユーザーでもストアド プロシージャを実行できます。</span><span class="sxs-lookup"><span data-stu-id="65fd4-106">Once a stored procedure is added by an assembly to the server or database context, any user can execute the stored procedure as long as the role for the user permits the actions performed by the stored procedure.</span></span>  
  
 <span data-ttu-id="65fd4-107">MDX でのストアド プロシージャの呼び出しは、固有の MDX 関数を呼び出す場合と同じ方法で行われます。</span><span class="sxs-lookup"><span data-stu-id="65fd4-107">Calling a stored procedure in MDX is done in the same manner as calling an intrinsic MDX function.</span></span> <span data-ttu-id="65fd4-108">パラメーターのないストアド プロシージャの場合は、次のようにストアド プロシージャ名と空のかっこを使用します。</span><span class="sxs-lookup"><span data-stu-id="65fd4-108">For a stored procedure that takes no parameters, the name of the procedure and an empty pair of parentheses are used, as shown here:</span></span>  
  
```  
MyStoredProcedure()  
```  
  
 <span data-ttu-id="65fd4-109">ストアド プロシージャに 1 つ以上のパラメーターを付ける場合は、それらをコンマで区切って順番に入力します。</span><span class="sxs-lookup"><span data-stu-id="65fd4-109">If the stored procedure takes one or more parameters, then the parameters are supplied, in order, separated by commas.</span></span> <span data-ttu-id="65fd4-110">次の例は、3 つのパラメーターがあるストアド プロシージャのサンプルを示しています。</span><span class="sxs-lookup"><span data-stu-id="65fd4-110">The following example demonstrates a sample stored procedure with three parameters:</span></span>  
  
```  
MyStoredProcedure("Parameter1", 2, 800)  
```  
  
## <a name="calling-stored-procedures-in-mdx-queries"></a><span data-ttu-id="65fd4-111">MDX クエリでストアド プロシージャを呼び出す</span><span class="sxs-lookup"><span data-stu-id="65fd4-111">Calling Stored Procedures in MDX Queries</span></span>  
 <span data-ttu-id="65fd4-112">MDX クエリでは必ず、MDX の式で必要とされる正しい構文の型をストアド プロシージャが返す必要があります。</span><span class="sxs-lookup"><span data-stu-id="65fd4-112">In all MDX queries, the stored procedure must return the syntactically correct type required by an MDX expression.</span></span> <span data-ttu-id="65fd4-113">ストアド プロシージャが正しい型を返さなければ、MDX のエラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="65fd4-113">If a stored procedure does not return the correct type, an MDX error occurs.</span></span> <span data-ttu-id="65fd4-114">次の例は、セット、メンバー、および数学的演算の結果を返すストアド プロシージャを示しています。</span><span class="sxs-lookup"><span data-stu-id="65fd4-114">The following examples demonstrate stored procedures that return a set, a member, and the result of a mathematical operation.</span></span>  
  
### <a name="returning-a-set"></a><span data-ttu-id="65fd4-115">セットを返す</span><span class="sxs-lookup"><span data-stu-id="65fd4-115">Returning a Set</span></span>  
 <span data-ttu-id="65fd4-116">次の例は、セットを返す MySproc というストアド プロシージャを実装します。</span><span class="sxs-lookup"><span data-stu-id="65fd4-116">The following examples implement a stored procedure, called MySproc, that returns a set.</span></span> <span data-ttu-id="65fd4-117">最初の例では、MySproc が SELECT 式でセットを直接返します。</span><span class="sxs-lookup"><span data-stu-id="65fd4-117">In the first example, MySproc returns the set directly in the SELECT expression.</span></span> <span data-ttu-id="65fd4-118">2 番目の 2 つの例では、MySproc が Crossjoin 関数と DrilldownLevel 関数の引数としてセットを返します。</span><span class="sxs-lookup"><span data-stu-id="65fd4-118">In the second two examples, MySproc returns the set as an argument for the Crossjoin and DrilldownLevel functions.</span></span>  
  
```  
SELECT MySetProcedure(a,b,c) ON 0 FROM Sales  
SELECT Crossjoin(MySetProcedure(a,b,c)) ON 0 FROM Sales  
SELECT DrilldownLevel(MySetProcedure(a,b,c)) ON 0 FROM Sales  
```  
  
### <a name="returning-a-member"></a><span data-ttu-id="65fd4-119">メンバーを返す</span><span class="sxs-lookup"><span data-stu-id="65fd4-119">Returning a Member</span></span>  
 <span data-ttu-id="65fd4-120">次の例は、メンバーを返す MySproc 関数を示しています。</span><span class="sxs-lookup"><span data-stu-id="65fd4-120">The following example shows a function MySproc function that returns a member:</span></span>  
  
```  
SELECT Descendants(MySproc(a,b,c),3) ON 0 FROM Sales  
```  
  
### <a name="returning-the-result-of-a-math-operation"></a><span data-ttu-id="65fd4-121">数学的演算の結果を返す</span><span class="sxs-lookup"><span data-stu-id="65fd4-121">Returning the Result of a Math Operation</span></span>  
  
```  
SELECT Country.Members on 0, MySproc(Measures.Sales) ON 1 FROM Sales  
```  
  
## <a name="calling-stored-procedures-with-the-call-statement"></a><span data-ttu-id="65fd4-122">Call ステートメントを使用したストアド プロシージャの呼び出し</span><span class="sxs-lookup"><span data-stu-id="65fd4-122">Calling Stored Procedures with the Call Statement</span></span>  
 <span data-ttu-id="65fd4-123">ストアド プロシージャは、MDX の `Call` ステートメントを使用して MDX クエリのコンテキスト外で呼び出すことが可能です。</span><span class="sxs-lookup"><span data-stu-id="65fd4-123">Stored procedures can be called outside of the context of an MDX query using the MDX `Call` statement.</span></span>  
  
 <span data-ttu-id="65fd4-124">このメソッドは、保存されているクエリの副作用をインスタンス化する場合や、保存されているクエリの結果をアプリケーションが取得する場合に使用できます。</span><span class="sxs-lookup"><span data-stu-id="65fd4-124">You can use this method to either instantiate the side effects of a stored query or for the application to get the results of a stored query.</span></span> <span data-ttu-id="65fd4-125">`Call` ステートメントは一般に、分析管理オブジェクト (AMO) を使用して、結果が返されない管理関数を実行するために使用します。</span><span class="sxs-lookup"><span data-stu-id="65fd4-125">A common use of the `Call` statement would be to use Analysis Management Objects (AMO) to perform administrative functions that do not have a return result.</span></span> <span data-ttu-id="65fd4-126">たとえば、次のコマンドはストアド プロシージャを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="65fd4-126">For example, the following command calls a stored procedure:</span></span>  
  
```  
Call MyStoredProcedure(a,b,c)  
```  
  
 <span data-ttu-id="65fd4-127">`Call` ステートメントでストアド プロシージャから返される型のうち、サポートされているものは行セットのみです。</span><span class="sxs-lookup"><span data-stu-id="65fd4-127">The only supported type returned from stored procedure in a `Call` statement is a rowset.</span></span> <span data-ttu-id="65fd4-128">行セットのシリアル化は XML forAnaysis で定義されます。</span><span class="sxs-lookup"><span data-stu-id="65fd4-128">The serialization for a rowset is defined by XML for Analysis.</span></span> <span data-ttu-id="65fd4-129">`Call` ステートメントのストアド プロシージャがその他の型を返した場合、それは無視され、XML で呼び出し元アプリケーションには返されません。</span><span class="sxs-lookup"><span data-stu-id="65fd4-129">If a stored procedure in a `Call` statement returns any other type, it is ignored and not returned in XML to the calling application.</span></span> <span data-ttu-id="65fd4-130">XML for Analysis 行セットの詳細については、「XML for Analysis のスキーマ行セット｣を参照してください。</span><span class="sxs-lookup"><span data-stu-id="65fd4-130">For more information about XML for Analysis rowsets, see, XML for Analysis Schema Rowsets.</span></span>  
  
 <span data-ttu-id="65fd4-131">ストアド プロシージャが .NET の行セットを返した場合、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] はサーバーの結果を XML for Analysis の行セットに変換します。</span><span class="sxs-lookup"><span data-stu-id="65fd4-131">If a stored procedure returns a .NET rowset, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] converts the result on the server to an XML for Analysis rowset.</span></span> <span data-ttu-id="65fd4-132">XML for Analysis の行セットは常に、`Call` 関数のストアド プロシージャによって返されます。</span><span class="sxs-lookup"><span data-stu-id="65fd4-132">The XML for Analysis rowset is always returned by a stored procedure in the `Call` function.</span></span> <span data-ttu-id="65fd4-133">XML for Analysis の行セットで表せない機能がデータセットに含まれている場合は、エラーが返されます。</span><span class="sxs-lookup"><span data-stu-id="65fd4-133">If a dataset contains features that cannot be expressed in the XML for Analysis rowset, a failure results.</span></span>  
  
 <span data-ttu-id="65fd4-134">無効な値を返すプロシージャ (たとえば、Visual Basic でのサブルーチン) も CALL キーワードと一緒に使用できます。</span><span class="sxs-lookup"><span data-stu-id="65fd4-134">Procedures that return void values (for example, subroutines in Visual Basic) can also be employed with the CALL keyword.</span></span> <span data-ttu-id="65fd4-135">たとえば、MDX ステートメントで MyVoidFunction() 関数を使用する場合は、次の構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="65fd4-135">If, for example, you wanted to use the function MyVoidFunction() in an MDX statement, the following syntax would be employed:</span></span>  
  
```  
CALL(MyVoidFunction)  
```  
  
## <a name="see-also"></a><span data-ttu-id="65fd4-136">参照</span><span class="sxs-lookup"><span data-stu-id="65fd4-136">See Also</span></span>  
 <span data-ttu-id="65fd4-137">[多次元モデルのアセンブリの管理](../multidimensional-models/multidimensional-model-assemblies-management.md) </span><span class="sxs-lookup"><span data-stu-id="65fd4-137">[Multidimensional Model Assemblies Management](../multidimensional-models/multidimensional-model-assemblies-management.md) </span></span>  
 [<span data-ttu-id="65fd4-138">ストアドプロシージャの定義</span><span class="sxs-lookup"><span data-stu-id="65fd4-138">Defining Stored Procedures</span></span>](../multidimensional-models-extending-olap-stored-procedures/defining-stored-procedures.md)  
  
  
