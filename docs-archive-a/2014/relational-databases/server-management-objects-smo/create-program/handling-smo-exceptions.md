---
title: SMO 例外の処理 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- SMO [SQL Server], exceptions
- exceptions [SMO]
- SQL Server Management Objects, exceptions
- inner exceptions [SMO]
ms.assetid: 4c725ff2-6588-44ca-b86a-87979e164153
author: stevestein
ms.author: sstein
ms.openlocfilehash: f4ae9e475a019c9bf874ee3f8365f3f3ac8e19d5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644946"
---
# <a name="handling-smo-exceptions"></a><span data-ttu-id="5dcb3-102">SMO 例外の処理</span><span class="sxs-lookup"><span data-stu-id="5dcb3-102">Handling SMO Exceptions</span></span>
  <span data-ttu-id="5dcb3-103">マネージド コードでは、エラーが発生すると例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="5dcb3-103">In managed code, exceptions are thrown when an error occurs.</span></span> <span data-ttu-id="5dcb3-104">SMO のメソッドやプロパティは、戻り値で成功や失敗をレポートしません。</span><span class="sxs-lookup"><span data-stu-id="5dcb3-104">SMO methods and properties do not report success or failure in the return value.</span></span> <span data-ttu-id="5dcb3-105">代わりに、例外ハンドラーによって例外のキャッチと処理を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="5dcb3-105">Instead, exceptions can be caught and handled by an exception handler.</span></span>  
  
 <span data-ttu-id="5dcb3-106">SMO にはさまざまな例外クラスが存在します。</span><span class="sxs-lookup"><span data-stu-id="5dcb3-106">Different exception classes exist in the SMO.</span></span> <span data-ttu-id="5dcb3-107">例外の詳細は、例外に関するテキスト メッセージを指定している `Message` プロパティなどの例外プロパティから抽出することができます。</span><span class="sxs-lookup"><span data-stu-id="5dcb3-107">Information about the exception can be extracted from the exception properties such as the `Message` property that gives a text message about the exception.</span></span>  
  
 <span data-ttu-id="5dcb3-108">例外処理ステートメントは、プログラミング言語に固有です。</span><span class="sxs-lookup"><span data-stu-id="5dcb3-108">The exception handling statements are specific to the programming language.</span></span> <span data-ttu-id="5dcb3-109">たとえば、[!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic では、`Catch` ステートメントとなります。</span><span class="sxs-lookup"><span data-stu-id="5dcb3-109">For example, in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic it is the `Catch` statement.</span></span>  
  
## <a name="inner-exceptions"></a><span data-ttu-id="5dcb3-110">内部例外</span><span class="sxs-lookup"><span data-stu-id="5dcb3-110">Inner Exceptions</span></span>  
 <span data-ttu-id="5dcb3-111">例外は、一般または固有のどちらかです。</span><span class="sxs-lookup"><span data-stu-id="5dcb3-111">Exceptions can either be general or specific.</span></span> <span data-ttu-id="5dcb3-112">一般例外には、固有の例外のセットが含まれています。</span><span class="sxs-lookup"><span data-stu-id="5dcb3-112">General exceptions contain a set of specific exceptions.</span></span> <span data-ttu-id="5dcb3-113">いくつかの `Catch` ステートメントを使用して、予想されるエラーの処理を行い、残りのエラーを一般例外の処理コードでは処理されないようにすることができます。</span><span class="sxs-lookup"><span data-stu-id="5dcb3-113">Several `Catch` statements can be used to handle anticipated errors and let remaining errors fall through to general exception handling code.</span></span> <span data-ttu-id="5dcb3-114">例外は、連鎖シーケンスによってしばしば発生します。</span><span class="sxs-lookup"><span data-stu-id="5dcb3-114">Exceptions often occur in a cascading sequence.</span></span> <span data-ttu-id="5dcb3-115">SMO 例外が、別の SQL 例外によって生じていることが少なくありません。</span><span class="sxs-lookup"><span data-stu-id="5dcb3-115">Frequently, an SMO exception might have been caused by an SQL exception.</span></span> <span data-ttu-id="5dcb3-116">これを検出する方法は、`InnerException` プロパティを連続的に使用して、最終的なトップレベル例外を発生している元の例外を判断します。</span><span class="sxs-lookup"><span data-stu-id="5dcb3-116">The way to detect this is to use the `InnerException` property successively to determine the original exception that caused the final, top-level exception.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5dcb3-117">この `SQLException` 例外は **、system.string**名前空間で宣言されています。</span><span class="sxs-lookup"><span data-stu-id="5dcb3-117">The `SQLException` exception is declared in the **System.Data.SqlClient** namespace.</span></span>  
  
 <span data-ttu-id="5dcb3-118">![例外が処理される各レベルを示す図](../../../database-engine/dev-guide/media/exception-flow.gif "例外が処理される各レベルを示す図")</span><span class="sxs-lookup"><span data-stu-id="5dcb3-118">![A diagram that shows the levels from which an excp](../../../database-engine/dev-guide/media/exception-flow.gif "A diagram that shows the levels from which an excp")</span></span>  
  
 <span data-ttu-id="5dcb3-119">このダイアグラムは、アプリケーションの層を通じた例外のフローを示しています。</span><span class="sxs-lookup"><span data-stu-id="5dcb3-119">The diagram shows the flow of exceptions through the layers of the application.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5dcb3-120">例</span><span class="sxs-lookup"><span data-stu-id="5dcb3-120">Example</span></span>  
 <span data-ttu-id="5dcb3-121">提供されているコード例を使用するには、アプリケーションを作成するプログラミング環境、プログラミング テンプレート、およびプログラミング言語を選択する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5dcb3-121">To use any code example that is provided, you will have to choose the programming environment, the programming template, and the programming language in which to create your application.</span></span> <span data-ttu-id="5dcb3-122">詳細については、「visual [studio .net で Visual C&#35; Smo プロジェクトを作成する](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md)」または「 [visual studio .NET で Visual Basic Smo プロジェクトを作成](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5dcb3-122">For more information, see [Create a Visual C&#35; SMO Project in Visual Studio .NET](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md) or [Create a Visual Basic SMO Project in Visual Studio .NET](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md).</span></span>  
  
## <a name="catching-an-exception-in-visual-basic"></a><span data-ttu-id="5dcb3-123">Visual Basic での例外のキャッチ</span><span class="sxs-lookup"><span data-stu-id="5dcb3-123">Catching an Exception in Visual Basic</span></span>  
 <span data-ttu-id="5dcb3-124">このコード例では、`Try...Catch...Finally`[!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] ステートメントを使用して SMO 例外をキャッチする方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="5dcb3-124">This code example shows how to use the `Try...Catch...Finally`[!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] statement to catch a SMO exception.</span></span> <span data-ttu-id="5dcb3-125">SMO 例外はすべて SmoException 型であり、これらは SMO のリファレンスに一覧されています。</span><span class="sxs-lookup"><span data-stu-id="5dcb3-125">All SMO exceptions have the type SmoException, and are listed in the SMO reference.</span></span> <span data-ttu-id="5dcb3-126">エラーの原因を示すために、内部例外のシーケンスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="5dcb3-126">The sequence of inner exceptions is displayed to show the root of the error.</span></span> <span data-ttu-id="5dcb3-127">詳細については、 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] .NET のマニュアルを参照してください。</span><span class="sxs-lookup"><span data-stu-id="5dcb3-127">For more information, see the [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] .NET documentation.</span></span>  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBExceptions1](SMO How to#SMO_VBExceptions1)]  -->  
  
## <a name="catching-an-exception-in-visual-c"></a><span data-ttu-id="5dcb3-128">Visual C# での例外のキャッチ</span><span class="sxs-lookup"><span data-stu-id="5dcb3-128">Catching an Exception in Visual C#</span></span>  
 <span data-ttu-id="5dcb3-129">このコード例では、`Try...Catch...Finally` Visual C# ステートメントを使用して SMO 例外をキャッチする方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="5dcb3-129">This code example shows how to use the `Try...Catch...Finally` Visual C# statement to catch a SMO exception.</span></span> <span data-ttu-id="5dcb3-130">SMO 例外はすべて SmoException 型であり、これらは SMO のリファレンスに一覧されています。</span><span class="sxs-lookup"><span data-stu-id="5dcb3-130">All SMO exceptions have the type SmoException, and are listed in the SMO reference.</span></span> <span data-ttu-id="5dcb3-131">エラーの原因を示すために、内部例外のシーケンスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="5dcb3-131">The sequence of inner exceptions is displayed to show the root of the error.</span></span> <span data-ttu-id="5dcb3-132">詳細については、C# のドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="5dcb3-132">For more information, see the Visual C# documentation.</span></span>  
  
```  
{   
//This sample requires the Microsoft.SqlServer.Management.Smo.Agent namespace to be included.   
//Connect to the local, default instance of SQL Server.   
Server srv;   
srv = new Server();   
//Define an Operator object variable by supplying the parent SQL Agent and the name arguments in the constructor.   
//Note that the Operator type requires [] parenthesis to differentiate it from a Visual Basic key word.   
op = new Operator(srv.JobServer, "Test_Operator");   
op.Create();   
//Start exception handling.   
try {   
    //Create the operator again to cause an SMO exception.   
    OperatorCategory opx;   
    opx = new OperatorCategory(srv.JobServer, "Test_Operator");   
    opx.Create();   
}   
//Catch the SMO exception   
catch (SmoException smoex) {   
    Console.WriteLine("This is an SMO Exception");   
   //Display the SMO exception message.   
   Console.WriteLine(smoex.Message);   
   //Display the sequence of non-SMO exceptions that caused the SMO exception.   
   Exception ex;   
   ex = smoex.InnerException;   
   while (!object.ReferenceEquals(ex.InnerException, (null))) {   
      Console.WriteLine(ex.InnerException.Message);   
      ex = ex.InnerException;   
    }   
    }   
   //Catch other non-SMO exceptions.   
   catch (Exception ex) {   
      Console.WriteLine("This is not an SMO exception.");   
}   
}  
```  
  
  
