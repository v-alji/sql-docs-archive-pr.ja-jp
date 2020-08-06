---
title: メソッドのバッチ処理 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- methods [Reporting Services], batches
- BatchHeader SOAP header
- Web service [Reporting Services], methods
- Report Server Web service, batching
- batches [Reporting Services]
- XML Web service [Reporting Services], methods
- locking [Reporting Services]
- multiple Web service methods
ms.assetid: 86435534-c9fe-4b49-b88c-7fb6d21976b0
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: c778da186fdbbfaed17b9635d9ca7309a369552b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644300"
---
# <a name="batching-methods"></a><span data-ttu-id="75abb-102">メソッドのバッチ処理</span><span class="sxs-lookup"><span data-stu-id="75abb-102">Batching Methods</span></span>
  <span data-ttu-id="75abb-103">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] の SOAP ヘッダーを使用することによって、1 つの操作に複数の Web サービス メソッドを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="75abb-103">The use of SOAP headers in [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] enables you to include multiple Web service methods in a single operation.</span></span> <span data-ttu-id="75abb-104">メソッドは、1 つのデータベース トランザクションのスコープ内で、呼び出された順序で実行されます。</span><span class="sxs-lookup"><span data-stu-id="75abb-104">Methods run within the scope of a single database transaction, in the order in which they are called.</span></span>  
  
 <span data-ttu-id="75abb-105">ロールバックは、複数メソッド バッチ操作の利点の 1 つです。</span><span class="sxs-lookup"><span data-stu-id="75abb-105">Rollback is one advantage of using multiple-method batch operations.</span></span> <span data-ttu-id="75abb-106">バッチの実行中にメソッド呼び出しでエラーが発生した場合は、レポート サーバーがバッチの実行を停止し、それ以前の操作をロールバックします。</span><span class="sxs-lookup"><span data-stu-id="75abb-106">If an error occurs on any of the method calls while a batch is running, the report server stops running the batch and rolls back any previous operations.</span></span> <span data-ttu-id="75abb-107">あるメソッドが、バッチ内の他のメソッド呼び出しの正常終了に依存している場合、この方法は便利です。</span><span class="sxs-lookup"><span data-stu-id="75abb-107">This is useful when a method call depends on the successful completion of other method calls in that batch.</span></span>  
  
 <span data-ttu-id="75abb-108">Web サービスは、複数メソッド バッチ操作に対するロック セマンティクスを提供しません。</span><span class="sxs-lookup"><span data-stu-id="75abb-108">The Web service does not provide locking semantics for multiple-method batch operations.</span></span> <span data-ttu-id="75abb-109">メッセージがサーバーに送信され、Execute コマンドが呼び出されるまでは、レポート サーバー データベースの行の更新がロックされません。</span><span class="sxs-lookup"><span data-stu-id="75abb-109">Rows in the report server database are not locked for updating until the message is sent to the server and the Execute command is called.</span></span>  
  
 <span data-ttu-id="75abb-110">データが最後に読み取られてからデータベースが変更されていないことを保証するコンカレンシー制御もありません。</span><span class="sxs-lookup"><span data-stu-id="75abb-110">There are also no concurrency controls to guarantee that the database has not changed since the data was last read.</span></span> <span data-ttu-id="75abb-111">2 台のクライアントが同じアイテムを変更する場合は、アイテムの名前が変更されていないなど、パラメーターが有効なままであれば最後の更新が成功します。</span><span class="sxs-lookup"><span data-stu-id="75abb-111">If two clients modify the same item, the last update succeeds if the parameters are still valid (for example, the item has not been renamed).</span></span>  
  
 <span data-ttu-id="75abb-112">次の例では、<xref:ReportService2005.ReportingService2005.CreateFolder%2A> メソッドを 3 回呼び出し、これらの呼び出しを 1 つのバッチとして実行します。</span><span class="sxs-lookup"><span data-stu-id="75abb-112">The following example calls the <xref:ReportService2005.ReportingService2005.CreateFolder%2A> method three times and runs these calls as a single batch.</span></span> <span data-ttu-id="75abb-113"><xref:ReportService2005.ReportingService2005.CreateFolder%2A> への呼び出しのいずれかが失敗すると、バッチ全体が取り消されます。</span><span class="sxs-lookup"><span data-stu-id="75abb-113">If any of the calls to <xref:ReportService2005.ReportingService2005.CreateFolder%2A> fail, the entire batch is canceled.</span></span>  
  
```vb  
Imports System  
Imports System.Web.Services.Protocols  
Imports myNamespace.MyReferenceName  
  
Class Sample  
    Sub Main(args() As String)  
        Dim rs As New ReportingService2005()  
        rs.Credentials = System.Net.CredentialCache.DefaultCredentials  
      ' Set the base Web service URL of the source server  
      rs.Url = "http://<Server Name>/reportserver/ReportService2005.asmx"  
  
        Dim bh As New BatchHeader()  
  
        bh.BatchId = service.CreateBatch()  
        rs.BatchHeaderValue = bh  
        rs.CreateFolder("New Folder1", "/", Nothing)  
        rs.CreateFolder("New Folder2", "/", Nothing)  
        rs.CreateFolder("New Folder3", "/", Nothing)  
  
        Console.WriteLine("Creating folders...")  
        rs.BatchHeaderValue = bh  
        rs.ExecuteBatch()  
        Console.WriteLine("Folders created successfully.")  
  
        rs.BatchHeaderValue = Nothing  
    End Sub  
End Class  
```  
  
```csharp  
using System;  
using System.Web.Services.Protocols;   
using myNamespace.MyReferenceName;  
  
class Sample  
{  
    static void Main(string[] args)  
    {  
        ReportingService2005 rs = new ReportingService2005();  
        rs.Credentials = System.Net.CredentialCache.DefaultCredentials;  
      // Set the base Web service URL of the source server  
      rs.Url = "http://<Server Name>/reportserver/ReportService2005.asmx"  
  
        BatchHeader bh = new BatchHeader();  
  
        bh1.BatchID = service.CreateBatch();  
        rs.BatchHeaderValue = bh;  
        rs.CreateFolder("New Folder1", "/", null);  
        rs.CreateFolder("New Folder2", "/", null);  
        rs.CreateFolder("New Folder3", "/", null);  
  
        Console.WriteLine("Creating folders...");  
        rs.BatchHeaderValue = bh1;  
        rs.ExecuteBatch();  
        Console.WriteLine("Folders created successfully.");  
  
        rs.BatchHeaderValue = null;  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="75abb-114">参照</span><span class="sxs-lookup"><span data-stu-id="75abb-114">See Also</span></span>  
 <xref:ReportService2005.ReportingService2005.CancelBatch%2A>   
 <xref:ReportService2005.ReportingService2005.CreateBatch%2A>   
 <span data-ttu-id="75abb-115">[SSRS&#41;&#40;テクニカルリファレンス](../technical-reference-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="75abb-115">[Technical Reference &#40;SSRS&#41;](../technical-reference-ssrs.md) </span></span>  
 [<span data-ttu-id="75abb-116">Reporting Services の SOAP ヘッダーの使用</span><span class="sxs-lookup"><span data-stu-id="75abb-116">Using Reporting Services SOAP Headers</span></span>](using-reporting-services-soap-headers.md)  
  
  
