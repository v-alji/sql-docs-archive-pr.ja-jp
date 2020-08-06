---
title: 接続の権限借用と資格情報 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- impersonation [CLR integration]
- security [CLR integration]
- database objects [CLR integration], connections
- connections [CLR integration]
- authentication [CLR integration]
- user impersonation [CLR integration]
- credentials [CLR integration]
- database objects [CLR integration], security
ms.assetid: 293dce7d-1db2-4657-992f-8c583d6e9ebb
author: rothja
ms.author: jroth
ms.openlocfilehash: cdbc52e07f4502adda7301ce7f635c050ed9c3c1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642125"
---
# <a name="impersonation-and-credentials-for-connections"></a><span data-ttu-id="b9887-102">接続の権限借用と資格情報</span><span class="sxs-lookup"><span data-stu-id="b9887-102">Impersonation and Credentials for Connections</span></span>
  <span data-ttu-id="b9887-103">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] CLR (共通言語ランタイム) 統合では、複雑な Windows 認証を使用する方が、SQL Server 認証を使用するよりもセキュリティが向上します。</span><span class="sxs-lookup"><span data-stu-id="b9887-103">In the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] common language runtime (CLR) integration, using Windows Authentication is complex, but is more secure than using SQL Server Authentication.</span></span> <span data-ttu-id="b9887-104">Windows 認証を使用する場合には、次の点を考慮してください。</span><span class="sxs-lookup"><span data-stu-id="b9887-104">When using Windows Authentication, keep in mind the following considerations.</span></span>  
  
 <span data-ttu-id="b9887-105">Windows に接続する SQL Server プロセスは、SQL Server Windows サービス アカウントのセキュリティ コンテキストを既定で取得します。</span><span class="sxs-lookup"><span data-stu-id="b9887-105">By default, a SQL Server process that connects out to Windows acquires the security context of the SQL Server Windows service account.</span></span> <span data-ttu-id="b9887-106">ただし、CLR 関数をプロキシ ID にマッピングすることにより、その発信接続に対し、Windows サービス アカウントとは異なるセキュリティ コンテキストを設定することができます。</span><span class="sxs-lookup"><span data-stu-id="b9887-106">But it is possible to map a CLR function to a proxy identity, so that its outbound connections have a different security context than that of the Windows service account.</span></span>  
  
 <span data-ttu-id="b9887-107">場合によっては、サービス アカウントで実行する代わりに、`SqlContext.WindowsIdentity` プロパティを使用して呼び出し元の権限を借用することもあります。</span><span class="sxs-lookup"><span data-stu-id="b9887-107">In some cases, you may want to impersonate the caller by using the `SqlContext.WindowsIdentity` property instead of running as the service account.</span></span> <span data-ttu-id="b9887-108">`WindowsIdentity` インスタンスは、呼び出し元のコードを実行するクライアントの ID を表し、クライアントで Windows 認証を使用する場合のみ入手できます。</span><span class="sxs-lookup"><span data-stu-id="b9887-108">The `WindowsIdentity` instance represents the identity of the client that invoked the calling code, and is only available when the client used Windows Authentication.</span></span> <span data-ttu-id="b9887-109">`WindowsIdentity` インスタンスを取得すると、`Impersonate` を呼び出してスレッドのセキュリティ トークンを変更し、その後でクライアントの代わりに ADO.NET 接続を開くことができます。</span><span class="sxs-lookup"><span data-stu-id="b9887-109">After you have obtained the `WindowsIdentity` instance, you can call `Impersonate` to change the security token of the thread, and then open ADO.NET connections on behalf of the client.</span></span>  
  
 <span data-ttu-id="b9887-110">WindowsIdentity を呼び出すと、ローカルデータにアクセスできなくなり、システムデータにアクセスできなくなります。</span><span class="sxs-lookup"><span data-stu-id="b9887-110">After you call SQLContext.WindowsIdentity.Impersonate, you cannot access local data and you cannot access system data.</span></span> <span data-ttu-id="b9887-111">データに再度アクセスするには、WindowsImpersonationContext を呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="b9887-111">To access data again, you have to call WindowsImpersonationContext.Undo.</span></span>  
  
 <span data-ttu-id="b9887-112">次の例では、`SqlContext.WindowsIdentity` プロパティを使用して呼び出し元の権限を借用します。</span><span class="sxs-lookup"><span data-stu-id="b9887-112">The following example shows how to impersonate the caller by using the `SqlContext.WindowsIdentity` property.</span></span>  
  
 <span data-ttu-id="b9887-113">Visual C#</span><span class="sxs-lookup"><span data-stu-id="b9887-113">Visual C#</span></span>  
  
```  
WindowsIdentity clientId = null;  
WindowsImpersonationContext impersonatedUser = null;  
  
clientId = SqlContext.WindowsIdentity;  
  
// This outer try block is used to protect from   
// exception filter attacks which would prevent  
// the inner finally block from executing and   
// resetting the impersonation.  
try  
{  
   try  
   {  
      impersonatedUser = clientId.Impersonate();  
      if (impersonatedUser != null)  
         return GetFileDetails(directoryPath);  
         else return null;  
   }  
   finally  
   {  
      if (impersonatedUser != null)  
         impersonatedUser.Undo();  
   }  
}  
catch  
{  
   throw;  
}  
```  
  
> [!NOTE]  
>  <span data-ttu-id="b9887-114">偽装における動作の変更点の詳細については、「 [SQL Server 2014 のデータベースエンジン機能における重大な変更](../../../database-engine/breaking-changes-to-database-engine-features-in-sql-server-2016.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b9887-114">For information about behavior changes in impersonation, see [Breaking Changes to Database Engine Features in SQL Server 2014](../../../database-engine/breaking-changes-to-database-engine-features-in-sql-server-2016.md).</span></span>  
  
 <span data-ttu-id="b9887-115">[!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows ID インスタンスを取得した場合、既定では、そのインスタンスを別のコンピューターに反映できません。既定では、Windows セキュリティ インフラストラクチャによりこの操作が制限されます。</span><span class="sxs-lookup"><span data-stu-id="b9887-115">Furthermore, if you obtained the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows identity instance, by default you cannot propagate that instance to another computer; Windows security infrastructure restricts that by default.</span></span> <span data-ttu-id="b9887-116">ただし、"委任" というメカニズムを使用すると、信頼関係のある複数のコンピューターに Windows ID を反映できるようになります。</span><span class="sxs-lookup"><span data-stu-id="b9887-116">There is, however, a mechanism called "delegation" that enables propagation of Windows identities across multiple trusted computers.</span></span> <span data-ttu-id="b9887-117">委任の詳細については、TechNet の記事「[Kerberos プロトコル遷移と制約付き委任](https://go.microsoft.com/fwlink/?LinkId=50419)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b9887-117">You can learn more about delegation in the TechNet article, "[Kerberos Protocol Transition and Constrained Delegation](https://go.microsoft.com/fwlink/?LinkId=50419)".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9887-118">参照</span><span class="sxs-lookup"><span data-stu-id="b9887-118">See Also</span></span>  
 [<span data-ttu-id="b9887-119">SqlContext オブジェクト</span><span class="sxs-lookup"><span data-stu-id="b9887-119">SqlContext Object</span></span>](../../clr-integration-data-access-in-process-ado-net/sqlcontext-object.md)  
  
  
