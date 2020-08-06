---
title: Reporting Services における SOAP の役割 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- Web service [Reporting Services], SOAP
- SOAP [Reporting Services], role in Reporting Services
- Report Server Web service, SOAP
- XML Web service [Reporting Services], SOAP
ms.assetid: f229c3ef-f2ca-448f-98f1-b8df350b9992
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 05445eb1c95c5761595944867b6d0c20a6f1a412
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87716097"
---
# <a name="the-role-of-soap-in-reporting-services"></a><span data-ttu-id="f3d9d-102">Reporting Services における SOAP の役割</span><span class="sxs-lookup"><span data-stu-id="f3d9d-102">The Role of SOAP in Reporting Services</span></span>
  <span data-ttu-id="f3d9d-103">レポート サーバー Web サービスでは、Simple Object Access Protocol (SOAP) メッセージングを使用し、ネットワーク経由でテキストベースのコマンドを送信します。</span><span class="sxs-lookup"><span data-stu-id="f3d9d-103">The Report Server Web service uses Simple Object Access Protocol (SOAP) messaging to send text-based commands over a network.</span></span> <span data-ttu-id="f3d9d-104">これらのコマンドは XML テキスト形式であり、HTTP を使用して World Wide Web 経由で送信されます。</span><span class="sxs-lookup"><span data-stu-id="f3d9d-104">These commands take the form of XML text that is sent over the World Wide Web using HTTP.</span></span> <span data-ttu-id="f3d9d-105">レポート サーバー Web サービスでは、通信プロトコルとして SOAP を使用することで、アプリケーションとコンポーネントが開放型で広く普及しているインフラストラクチャを使用してレポート サーバーとデータを交換できるようにしています。</span><span class="sxs-lookup"><span data-stu-id="f3d9d-105">By using SOAP as its communication protocol, the Report Server Web service allows applications and components to exchange data with the report server using an open and widely accepted infrastructure.</span></span> <span data-ttu-id="f3d9d-106">SOAP 標準は www.w3.org/TR/SOAP で定義されています。</span><span class="sxs-lookup"><span data-stu-id="f3d9d-106">The SOAP standard is defined at www.w3.org/TR/SOAP.</span></span>  
  
 <span data-ttu-id="f3d9d-107">クライアント アプリケーションは、SOAP に対応しており、SOAP 要求を送信できる限り、SOAP クライアントして動作できます。</span><span class="sxs-lookup"><span data-stu-id="f3d9d-107">Any client application can act as a SOAP client as long as it is SOAP-aware and can send SOAP requests.</span></span> <span data-ttu-id="f3d9d-108">レポート マネージャーはそのような SOAP クライアントの 1 つです。</span><span class="sxs-lookup"><span data-stu-id="f3d9d-108">Report Manager is one such SOAP client.</span></span> <span data-ttu-id="f3d9d-109">レポート マネージャーは、すべてのレポートとレポート関連コンテンツが格納されているレポート サーバー データベースへのインターフェイスを提供します。</span><span class="sxs-lookup"><span data-stu-id="f3d9d-109">It provides an interface to the report server database in which all reports and report-related content is stored.</span></span> <span data-ttu-id="f3d9d-110">エンド ユーザーはアプリケーションを使用して、レポート サーバー名前空間のレポートとフォルダーを参照し、管理できます。</span><span class="sxs-lookup"><span data-stu-id="f3d9d-110">End users can use the application to browse through and manage reports and folders in the report server namespace.</span></span> <span data-ttu-id="f3d9d-111">レポート マネージャーはレポート サーバー Web サービス インフラストラクチャ上に構築されています。</span><span class="sxs-lookup"><span data-stu-id="f3d9d-111">Report Manager is built on the Report Server Web service infrastructure.</span></span>  
  
 <span data-ttu-id="f3d9d-112">レポート サーバーは SOAP サーバーとして動作します。SOAP サーバーは、SOAP クライアントから要求を受け取り、適切な応答を作成できる SOAP 対応サービスです。</span><span class="sxs-lookup"><span data-stu-id="f3d9d-112">A report server acts as a SOAP server, a SOAP-aware service that can accept requests from SOAP clients and create appropriate responses.</span></span> <span data-ttu-id="f3d9d-113">サーバーは要求を処理し、クライアントにエンコードされた応答を送り返します。</span><span class="sxs-lookup"><span data-stu-id="f3d9d-113">The server handles the requests and sends encoded responses back to the client.</span></span>  
  
 <span data-ttu-id="f3d9d-114">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] の SOAP メッセージは、クライアントで行われた要求の種類によってさまざまな形式を取ります。</span><span class="sxs-lookup"><span data-stu-id="f3d9d-114">SOAP messages in [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] take many different forms, depending on the type of request made by the client.</span></span> <span data-ttu-id="f3d9d-115">次の例は、レポート サーバー データベースからアイテムを削除する簡単な SOAP クライアント要求を表しています。</span><span class="sxs-lookup"><span data-stu-id="f3d9d-115">The following example represents a simple SOAP client request to remove an item from the report server database.</span></span>  
  
```  
<soap:Envelope xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema">  
    <soap:Body>  
        <DeleteItem xmlns="https://www.microsoft.com/sql/ReportingServer">  
            <item>/Samples/Report1</item>  
        </DeleteItem>  
    </soap:Body>  
</soap:Envelope>  
```  
  
 <span data-ttu-id="f3d9d-116">SOAP 自体は、メッセージを `Envelope` 要素に入れるよう要求します。メッセージは一括して `Body` 要素内に入ります。</span><span class="sxs-lookup"><span data-stu-id="f3d9d-116">The SOAP itself requires that messages be put into an `Envelope` element, with the bulk of the message inside a `Body` element.</span></span> <span data-ttu-id="f3d9d-117">この例では、Body には <xref:ReportService2010.ReportingService2010.DeleteItem%2A> メソッドの呼び出しが入っています。このメソッドは、削除するアイテムのパスを表す文字列パラメーターを取ります。</span><span class="sxs-lookup"><span data-stu-id="f3d9d-117">In this example, the body contains a call to the <xref:ReportService2010.ReportingService2010.DeleteItem%2A> method, which takes a string parameter representing the path of the item to delete.</span></span> <span data-ttu-id="f3d9d-118">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] すべての SOAP 操作をメソッドにカプセル化するクライアントプロキシクラスを作成できます。</span><span class="sxs-lookup"><span data-stu-id="f3d9d-118">You can create a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] client proxy class that encapsulates all SOAP operations into methods.</span></span> <span data-ttu-id="f3d9d-119">次のメソッドは、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[csprcs](../../includes/csprcs-md.md)] 前に示した SOAP の例を表しています。</span><span class="sxs-lookup"><span data-stu-id="f3d9d-119">The following [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[csprcs](../../includes/csprcs-md.md)] method represents the SOAP example given earlier.</span></span>  
  
```  
public void DeleteItem(string item);  
```  
  
 <span data-ttu-id="f3d9d-120">サーバーからの応答は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="f3d9d-120">The response from the server might look like the following:</span></span>  
  
```  
<soap:Envelope xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema">  
    <soap:Body>  
        <DeleteItemResponse xmlns="https://www.microsoft.com/sql/ReportingServer" />  
    </soap:Body>  
</soap:Envelope>  
```  
  
 <span data-ttu-id="f3d9d-121"><xref:ReportService2010.ReportingService2010.DeleteItem%2A> メソッドに戻り値はないため、空の応答が返されます。</span><span class="sxs-lookup"><span data-stu-id="f3d9d-121">The <xref:ReportService2010.ReportingService2010.DeleteItem%2A> method has no return value, so an empty response is returned.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3d9d-122">参照</span><span class="sxs-lookup"><span data-stu-id="f3d9d-122">See Also</span></span>  
 <span data-ttu-id="f3d9d-123">[SOAP API へのアクセス](accessing-the-soap-api.md) </span><span class="sxs-lookup"><span data-stu-id="f3d9d-123">[Accessing the SOAP API](accessing-the-soap-api.md) </span></span>  
 <span data-ttu-id="f3d9d-124">[レポート マネージャー &#40;SSRS ネイティブ モード&#41;](../report-manager-ssrs-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="f3d9d-124">[Report Manager  &#40;SSRS Native Mode&#41;](../report-manager-ssrs-native-mode.md) </span></span>  
 <span data-ttu-id="f3d9d-125">[レポートサーバーの Reporting Services](../reporting-services-report-server.md) </span><span class="sxs-lookup"><span data-stu-id="f3d9d-125">[Reporting Services Report Server](../reporting-services-report-server.md) </span></span>  
 [<span data-ttu-id="f3d9d-126">レポート サーバー web サービス</span><span class="sxs-lookup"><span data-stu-id="f3d9d-126">Report Server Web Service</span></span>](report-server-web-service.md)  
  
  
