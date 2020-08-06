---
title: SqlContext オブジェクト |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- Windows identity [CLR integration]
- SqlContext object
- context [CLR integration]
ms.assetid: 67437853-8a55-44d9-9337-90689ebba730
author: rothja
ms.author: jroth
ms.openlocfilehash: 10f036e274925f7b28b79f619f8e24b3e8804140
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87718267"
---
# <a name="sqlcontext-object"></a><span data-ttu-id="63070-102">SqlContext オブジェクト</span><span class="sxs-lookup"><span data-stu-id="63070-102">SqlContext Object</span></span>
  <span data-ttu-id="63070-103">プロシージャや関数の呼び出し時、CLR (共通言語ランタイム) ユーザー定義型のメソッドの呼び出し時、または任意の [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework 言語で定義されたトリガーの起動時には、サーバーのマネージド コードを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="63070-103">You invoke managed code in the server when you call a procedure or function, when you call a method on a common language runtime (CLR) user-defined type, or when your action fires a trigger defined in any of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework languages.</span></span> <span data-ttu-id="63070-104">このコードの実行はユーザー接続の一環として要求されるので、サーバーで実行しているコードから呼び出し元のコンテキストにアクセスできる必要があります。</span><span class="sxs-lookup"><span data-stu-id="63070-104">Because execution of this code is requested as part of a user connection, access to the context of the caller from the code running in the server is required.</span></span> <span data-ttu-id="63070-105">また、特定のデータ アクセス操作には、コードが呼び出し元のコンテキストで実行されている場合にしか有効にならないものもあります。</span><span class="sxs-lookup"><span data-stu-id="63070-105">In addition, certain data access operations may only be valid if run under the context of the caller.</span></span> <span data-ttu-id="63070-106">たとえば、トリガー操作で使用される inserted 擬似テーブルや deleted 擬似テーブルにアクセスするには、コードが呼び出し元のコンテキストで実行されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="63070-106">For example, access to inserted and deleted pseudo-tables used in trigger operations is only valid under the context of the caller.</span></span>  
  
 <span data-ttu-id="63070-107">呼び出し側のコンテキストは、`SqlContext` オブジェクト内で抽象化されています。</span><span class="sxs-lookup"><span data-stu-id="63070-107">The context of the caller is abstracted in a `SqlContext` object.</span></span> <span data-ttu-id="63070-108">`SqlTriggerContext` メソッドおよびプロパティの詳細については、[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK の `Microsoft.SqlServer.Server.SqlTriggerContext` クラスのリファレンス ドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="63070-108">For more information about the `SqlTriggerContext` methods and properties, see the `Microsoft.SqlServer.Server.SqlTriggerContext` class reference documentation in the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK.</span></span>  
  
 <span data-ttu-id="63070-109">`SqlContext` は、次のコンポーネントへのアクセスを提供します。</span><span class="sxs-lookup"><span data-stu-id="63070-109">`SqlContext` provides access to the following components:</span></span>  
  
-   <span data-ttu-id="63070-110">`SqlPipe`: 結果をクライアントに送信するのに使用する "パイプ" を表す `SqlPipe` オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="63070-110">`SqlPipe`: The `SqlPipe` object represents the "pipe" through which results flow to the client.</span></span> <span data-ttu-id="63070-111">オブジェクトの詳細については `SqlPipe` 、「 [SqlPipe オブジェクト](sqlpipe-object.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="63070-111">For more information about the `SqlPipe` object, see [SqlPipe Object](sqlpipe-object.md).</span></span>  
  
-   <span data-ttu-id="63070-112">`SqlTriggerContext`: `SqlTriggerContext` オブジェクトは、CLR トリガー内でしか取得できません。</span><span class="sxs-lookup"><span data-stu-id="63070-112">`SqlTriggerContext`: The `SqlTriggerContext` object can only be retrieved from within a CLR trigger.</span></span> <span data-ttu-id="63070-113">このオブジェクトでは、トリガーを起動した操作や、更新された列のマップについての情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="63070-113">It provides information about the operation that caused the trigger to fire and a map of the columns that were updated.</span></span> <span data-ttu-id="63070-114">オブジェクトの詳細については `SqlTriggerContext` 、「 [Sqltriggercontext オブジェクト](sqltriggercontext-object.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="63070-114">For more information about the `SqlTriggerContext` object, see [SqlTriggerContext Object](sqltriggercontext-object.md).</span></span>  
  
-   <span data-ttu-id="63070-115">`IsAvailable`: `IsAvailable` プロパティはコンテキスト可用性を判断するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="63070-115">`IsAvailable`: The `IsAvailable` property is used to determine context availability.</span></span>  
  
-   <span data-ttu-id="63070-116">`WindowsIdentity`: `WindowsIdentity` プロパティは呼び出し元の Windows ID を取得するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="63070-116">`WindowsIdentity`: The `WindowsIdentity` property is used to retrieve the Windows identity of the caller.</span></span>  
  
## <a name="determining-context-availability"></a><span data-ttu-id="63070-117">コンテキスト可用性の判断</span><span class="sxs-lookup"><span data-stu-id="63070-117">Determining Context Availability</span></span>  
 <span data-ttu-id="63070-118">`SqlContext` クラスをクエリすると、現在実行しているコードがインプロセスで実行されているかどうかを判定できます。</span><span class="sxs-lookup"><span data-stu-id="63070-118">Query the `SqlContext` class to see if the currently executing code is running in-process.</span></span> <span data-ttu-id="63070-119">これを行うには、`IsAvailable` オブジェクトの `SqlContext` プロパティを確認します。</span><span class="sxs-lookup"><span data-stu-id="63070-119">To do this, check the `IsAvailable` property of the `SqlContext` object.</span></span> <span data-ttu-id="63070-120">`IsAvailable` プロパティは読み取り専用で、呼び出し元のコードが [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 内で実行されており、他の `True` メンバーにアクセスできる場合は、`SqlContext` を返します。</span><span class="sxs-lookup"><span data-stu-id="63070-120">The `IsAvailable` property is read-only, and returns `True` if the calling code is running inside [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and if other `SqlContext` members can be accessed.</span></span> <span data-ttu-id="63070-121">`IsAvailable` プロパティから `False` が返された場合、他のすべての `SqlContext` メンバーから `InvalidOperationException` がスローされます (ただし、この例外が使用されている場合に限ります)。</span><span class="sxs-lookup"><span data-stu-id="63070-121">If the `IsAvailable` property returns `False`, all the other `SqlContext` members throw an `InvalidOperationException`, if used.</span></span> <span data-ttu-id="63070-122">`IsAvailable` プロパティから `False` が返された場合、接続文字列で "context connection=true" が指定されている接続オブジェクトを開く操作は失敗します。</span><span class="sxs-lookup"><span data-stu-id="63070-122">If `IsAvailable` returns `False`, any attempt to open a connection object that has "context connection=true" in the connection string fails.</span></span>  
  
## <a name="retrieving-windows-identity"></a><span data-ttu-id="63070-123">Windows ID の取得</span><span class="sxs-lookup"><span data-stu-id="63070-123">Retrieving Windows Identity</span></span>  
 <span data-ttu-id="63070-124">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 内で実行されている CLR コードは、常に、プロセス アカウントのコンテキストで呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="63070-124">CLR code executing inside [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is always invoked in the context of the process account.</span></span> <span data-ttu-id="63070-125">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] プロセス ID ではなく、呼び出し元ユーザーの ID を使用して特定の操作を行う必要がある場合は、`WindowsIdentity` オブジェクトの `SqlContext` メソッドにより権限借用トークンを取得する必要があります。</span><span class="sxs-lookup"><span data-stu-id="63070-125">If the code should perform certain actions using the identity of the calling user, instead of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] process identity, then an impersonation token should be obtained through the `WindowsIdentity` property of the `SqlContext` object.</span></span> <span data-ttu-id="63070-126">`WindowsIdentity` プロパティは、呼び出し元ユーザーの [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows ID を表す `WindowsIdentity` インスタンスを返します。クライアントが [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証を使用して認証されている場合は、NULL を返します。</span><span class="sxs-lookup"><span data-stu-id="63070-126">The `WindowsIdentity` property returns a `WindowsIdentity` instance representing the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows identity of the caller, or null if the client was authenticated using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span> <span data-ttu-id="63070-127">`EXTERNAL_ACCESS` 権限または `UNSAFE` 権限のあるアセンブリのみが、このプロパティにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="63070-127">Only assemblies marked with `EXTERNAL_ACCESS` or `UNSAFE` permissions can access this property.</span></span>  
  
 <span data-ttu-id="63070-128">`WindowsIdentity` オブジェクトの取得後、呼び出し元は、クライアント アカウントの権限を借用して、操作を実行できます。</span><span class="sxs-lookup"><span data-stu-id="63070-128">After obtaining the `WindowsIdentity` object, callers can impersonate the client account and perform actions on their behalf.</span></span>  
  
 <span data-ttu-id="63070-129">ストアド プロシージャまたは関数の実行を開始したユーザーが Windows 認証を使用してサーバーに接続している場合、`SqlContext.WindowsIdentity` が呼び出し元ユーザーの ID を取得する唯一の手段となります。</span><span class="sxs-lookup"><span data-stu-id="63070-129">The identity of the caller is only available through `SqlContext.WindowsIdentity` if the client that initiated execution of the stored-procedure or function connected to the server using Windows Authentication.</span></span> <span data-ttu-id="63070-130">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証が使用されている場合、このプロパティは NULL になり、コードでは呼び出し元ユーザーの権限を借用することはできません。</span><span class="sxs-lookup"><span data-stu-id="63070-130">If [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication was used instead, this property is null and the code is unable to impersonate the caller.</span></span>  
  
### <a name="example"></a><span data-ttu-id="63070-131">例</span><span class="sxs-lookup"><span data-stu-id="63070-131">Example</span></span>  
 <span data-ttu-id="63070-132">次の例では、呼び出し元であるクライアントの Windows ID を取得し、クライアントの権限を借用する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="63070-132">The following example shows how to get the Windows identity of the calling client and impersonate the client.</span></span>  
  
 <span data-ttu-id="63070-133">C#</span><span class="sxs-lookup"><span data-stu-id="63070-133">C#</span></span>  
  
```  
[Microsoft.SqlServer.Server.SqlProcedure]  
public static void WindowsIDTestProc()  
{  
    WindowsIdentity clientId = null;  
    WindowsImpersonationContext impersonatedUser = null;  
  
    // Get the client ID.  
    clientId = SqlContext.WindowsIdentity;  
  
    // This outer try block is used to thwart exception filter   
    // attacks which would prevent the inner finally   
    // block from executing and resetting the impersonation.  
    try  
    {  
        try  
        {  
            impersonatedUser = clientId.Impersonate();  
            if (impersonatedUser != null)  
            {  
                // Perform some action using impersonation.  
            }  
        }  
        finally  
        {  
            // Undo impersonation.  
            if (impersonatedUser != null)  
                impersonatedUser.Undo();  
        }  
    }  
    catch  
    {  
        throw;  
    }  
}  
```  
  
 <span data-ttu-id="63070-134">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="63070-134">Visual Basic</span></span>  
  
```  
<Microsoft.SqlServer.Server.SqlProcedure()> _  
Public Shared Sub  WindowsIDTestProcVB ()  
    Dim clientId As WindowsIdentity  
    Dim impersonatedUser As WindowsImpersonationContext  
  
    ' Get the client ID.  
    clientId = SqlContext.WindowsIdentity  
  
    ' This outer try block is used to thwart exception filter   
    ' attacks which would prevent the inner finally   
    ' block from executing and resetting the impersonation.  
  
    Try  
        Try  
  
            impersonatedUser = clientId.Impersonate()  
  
            If impersonatedUser IsNot Nothing Then  
                ' Perform some action using impersonation.  
            End If  
  
        Finally  
            ' Undo impersonation.  
            If impersonatedUser IsNot Nothing Then  
                impersonatedUser.Undo()  
            End If  
        End Try  
  
    Catch e As Exception  
  
        Throw e  
  
    End Try  
End Sub  
```  
  
## <a name="see-also"></a><span data-ttu-id="63070-135">参照</span><span class="sxs-lookup"><span data-stu-id="63070-135">See Also</span></span>  
 <span data-ttu-id="63070-136">[SqlPipe オブジェクト](sqlpipe-object.md) </span><span class="sxs-lookup"><span data-stu-id="63070-136">[SqlPipe Object](sqlpipe-object.md) </span></span>  
 <span data-ttu-id="63070-137">[SqlTriggerContext オブジェクト](sqltriggercontext-object.md) </span><span class="sxs-lookup"><span data-stu-id="63070-137">[SqlTriggerContext Object](sqltriggercontext-object.md) </span></span>  
 <span data-ttu-id="63070-138">[CLR トリガー](../../database-engine/dev-guide/clr-triggers.md) </span><span class="sxs-lookup"><span data-stu-id="63070-138">[CLR Triggers](../../database-engine/dev-guide/clr-triggers.md) </span></span>  
 [<span data-ttu-id="63070-139">ADO.NET に対する SQL Server インプロセス固有の拡張機能</span><span class="sxs-lookup"><span data-stu-id="63070-139">SQL Server In-Process Specific Extensions to ADO.NET</span></span>](sql-server-in-process-specific-extensions-to-ado-net.md)  
  
  
