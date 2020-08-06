---
title: 接続とセッションの管理 (XMLA) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- statefulness [XML for Analysis]
- statelessness [XML for Analysis]
- XML for Analysis, sessions
- states [XML for Analysis]
- XMLA, sessions
- sessions [XML for Analysis]
ms.assetid: b83bb3ff-09be-4fda-9d1d-6248e04ffb21
author: minewiskan
ms.author: owend
ms.openlocfilehash: 7bfe876f6874193fd0885f16d91caa9f6fe8b172
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639731"
---
# <a name="managing-connections-and-sessions-xmla"></a><span data-ttu-id="b2795-102">接続およびセッションの管理 (XMLA)</span><span class="sxs-lookup"><span data-stu-id="b2795-102">Managing Connections and Sessions (XMLA)</span></span>
  <span data-ttu-id="b2795-103">*状態保持*は、サーバーがメソッド呼び出し間でクライアントの id とコンテキストを保持する条件です。</span><span class="sxs-lookup"><span data-stu-id="b2795-103">*Statefulness* is a condition during which the server preserves the identity and context of a client between method calls.</span></span> <span data-ttu-id="b2795-104">*状態*は、メソッドの呼び出しが完了した後に、サーバーがクライアントの id とコンテキストを記憶しない条件です。</span><span class="sxs-lookup"><span data-stu-id="b2795-104">*Statelessness* is a condition during which the server does not remember the identity and context of a client after a method call finishes.</span></span>  
  
 <span data-ttu-id="b2795-105">状態保持を提供するために、XML for Analysis (XMLA) は、一連のステートメントをまとめて実行できる*セッション*をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="b2795-105">To provide statefulness, XML for Analysis (XMLA) supports *sessions* that allow a series of statements to be performed together.</span></span> <span data-ttu-id="b2795-106">そのような一連のステートメントの例としては、後続のクエリで使用するための計算されるメンバーの作成があります。</span><span class="sxs-lookup"><span data-stu-id="b2795-106">An example of such a series of statements would be the creation of a calculated member that is to be used in subsequent queries.</span></span>  
  
 <span data-ttu-id="b2795-107">一般に、XMLA のセッションは、OLE DB 2.6 の仕様で概説されている以下の動作に従います。</span><span class="sxs-lookup"><span data-stu-id="b2795-107">In general, sessions in XMLA follow the following behavior outlined by the OLE DB 2.6 specification:</span></span>  
  
-   <span data-ttu-id="b2795-108">セッションはトランザクションとコマンド コンテキストのスコープを定義します。</span><span class="sxs-lookup"><span data-stu-id="b2795-108">Sessions define transaction and command context scope.</span></span>  
  
-   <span data-ttu-id="b2795-109">複数のコマンドを単一のセッションのコンテキストで実行できます。</span><span class="sxs-lookup"><span data-stu-id="b2795-109">Multiple commands can be run in the context of a single session.</span></span>  
  
-   <span data-ttu-id="b2795-110">XMLA コンテキストでのトランザクションのサポートは、 [Execute](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-execute)メソッドと共に送信されるプロバイダー固有のコマンドを介して行われます。</span><span class="sxs-lookup"><span data-stu-id="b2795-110">Support for transactions in the XMLA context is through provider-specific commands sent with the [Execute](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-execute) method.</span></span>  
  
 <span data-ttu-id="b2795-111">XMLA は、Distributed Authoring and Versioning (DAV) プロトコルが疎結合環境でロックを実装するために使用しているアプローチと同様の手法で、Web 環境のセッションをサポートする方法を定義します。</span><span class="sxs-lookup"><span data-stu-id="b2795-111">XMLA defines a way to support sessions in a Web environment in a mode similar to the approach used by the Distributed Authoring and Versioning (DAV) protocol to implement locking in a loosely coupled environment.</span></span> <span data-ttu-id="b2795-112">この実装は、プロバイダーがさまざまな理由 (たとえば、タイムアウトや接続エラーなど) でセッションの有効期限を終了させることができるという点で、DAV と類似しています。</span><span class="sxs-lookup"><span data-stu-id="b2795-112">This implementation parallels DAV in that the provider is allowed to expire sessions for various reasons (for example, a timeout or connection error).</span></span> <span data-ttu-id="b2795-113">セッションがサポートされる場合、Web サービスは、中断されて再開が必要なコマンドのセットを認識し、処理する準備を整えている必要があります。</span><span class="sxs-lookup"><span data-stu-id="b2795-113">When sessions are supported, Web services must be aware and ready to handle interrupted sets of commands that must be restarted.</span></span>  
  
 <span data-ttu-id="b2795-114">World Wide Web Consortium (W3C) による Simple Object Access Protocol (SOAP) 仕様は、新しいプロトコルを作成するには SOAP メッセージの先頭に SOAP ヘッダーを使用することを推奨しています。</span><span class="sxs-lookup"><span data-stu-id="b2795-114">The World Wide Web Consortium (W3C) Simple Object Access Protocol (SOAP) specification recommends using SOAP headers for building up new protocols on top of SOAP messages.</span></span> <span data-ttu-id="b2795-115">次の表は、XMLA がセッションの開始、維持、終了のために定義する SOAP ヘッダー要素と属性の一覧を示しています。</span><span class="sxs-lookup"><span data-stu-id="b2795-115">The following table lists the SOAP header elements and attributes that XMLA defines for initiating, maintaining, and closing a session.</span></span>  
  
|<span data-ttu-id="b2795-116">SOAP ヘッダー</span><span class="sxs-lookup"><span data-stu-id="b2795-116">SOAP header</span></span>|<span data-ttu-id="b2795-117">説明</span><span class="sxs-lookup"><span data-stu-id="b2795-117">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="b2795-118">BeginSession</span><span class="sxs-lookup"><span data-stu-id="b2795-118">BeginSession</span></span>|<span data-ttu-id="b2795-119">プロバイダーに新しいセッションの作成を要求します。</span><span class="sxs-lookup"><span data-stu-id="b2795-119">This header requests the provider to create a new session.</span></span> <span data-ttu-id="b2795-120">プロバイダーは、新しいセッションを作成し、SOAP 応答の Session ヘッダーの一部としてセッション ID を返すことによって応答します。</span><span class="sxs-lookup"><span data-stu-id="b2795-120">The provider should respond by constructing a new session and returning the session ID as part of the Session header in the SOAP response.</span></span>|  
|<span data-ttu-id="b2795-121">SessionId</span><span class="sxs-lookup"><span data-stu-id="b2795-121">SessionId</span></span>|<span data-ttu-id="b2795-122">値域には、セッションの残りの部分での各メソッド呼び出しで使用する必要のあるセッション ID が含まれます。</span><span class="sxs-lookup"><span data-stu-id="b2795-122">The value area contains the session ID that must be used in each method call for the rest of the session.</span></span> <span data-ttu-id="b2795-123">プロバイダーは SOAP 応答の中でこのタグを送信します。クライアントも、Session ヘッダー要素ごとに、この属性を送信する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b2795-123">The provider in the SOAP response sends this tag and the client must also send this attribute with each Session header element.</span></span>|  
|<span data-ttu-id="b2795-124">Session</span><span class="sxs-lookup"><span data-stu-id="b2795-124">Session</span></span>|<span data-ttu-id="b2795-125">このヘッダーは、セッションで生じるメソッド呼び出しごとに使用する必要があります。値域にはセッション ID が含まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="b2795-125">For every method call that occurs in the session, this header must be used, and the session ID must be included in the value area of the header.</span></span>|  
|<span data-ttu-id="b2795-126">EndSession</span><span class="sxs-lookup"><span data-stu-id="b2795-126">EndSession</span></span>|<span data-ttu-id="b2795-127">セッションを終了するには、このヘッダーを使用します。</span><span class="sxs-lookup"><span data-stu-id="b2795-127">To terminate the session, use this header.</span></span> <span data-ttu-id="b2795-128">セッション ID がこの値域に含まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="b2795-128">The session ID must be included with the value area.</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="b2795-129">セッション ID は、そのセッションが引き続き有効であることを保証するものではありません。</span><span class="sxs-lookup"><span data-stu-id="b2795-129">A session ID does not guarantee that a session stays valid.</span></span> <span data-ttu-id="b2795-130">セッションの有効期限が切れた場合 (たとえば、タイムアウトが生じた場合や、接続が失われた場合など)、プロバイダーはそのセッションのアクションを終了してロールバックすることができます。</span><span class="sxs-lookup"><span data-stu-id="b2795-130">If the session expires (for example, if it times out or the connection is lost), the provider can choose to end and roll back that session's actions.</span></span> <span data-ttu-id="b2795-131">その結果、同じセッション ID でのクライアントからの後続のメソッド呼び出しはすべて、セッションが有効でないことを示すエラーによって失敗します。</span><span class="sxs-lookup"><span data-stu-id="b2795-131">As a result, all subsequent method calls from the client on a session ID fail with an error signaling a session that is not valid.</span></span> <span data-ttu-id="b2795-132">クライアントは、この状況に対処し、そのセッションのメソッド呼び出しを最初から再送信するよう準備する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b2795-132">A client should handle this condition and be prepared to resend the session method calls from the beginning.</span></span>  
  
## <a name="legacy-code-example"></a><span data-ttu-id="b2795-133">レガシ コードの例</span><span class="sxs-lookup"><span data-stu-id="b2795-133">Legacy Code Example</span></span>  
 <span data-ttu-id="b2795-134">以下の例は、セッションがどのようにサポートされるかを示しています。</span><span class="sxs-lookup"><span data-stu-id="b2795-134">The following example shows how sessions are supported.</span></span>  
  
1.  <span data-ttu-id="b2795-135">セッションを開始するには、クライアントからのアウトバウンド XMLA メソッド呼び出しに SOAP の BeginSession ヘッダーを追加します。</span><span class="sxs-lookup"><span data-stu-id="b2795-135">To begin the session, add a BeginSession header in SOAP to the outbound XMLA method call from the client.</span></span> <span data-ttu-id="b2795-136">セッション ID がまだ不明なため、値域が最初は空白になっています。</span><span class="sxs-lookup"><span data-stu-id="b2795-136">The value area is initially blank because the session ID is not yet known.</span></span>  
  
    ```  
    <SOAP-ENV:Envelope  
       xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/"  
       SOAP-ENV:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/">  
       <SOAP-ENV:Header>  
          <XA:BeginSession  
             xmlns:XA="urn:schemas-microsoft-com:xml-analysis"  
             xsi:type="xsd:int"  
             mustUnderstand="1"/>  
       </SOAP-ENV:Header>  
       <SOAP-ENV:Body>  
          ...<!-- Discover or Execute call goes here.-->  
       </SOAP-ENV:Body>  
    </SOAP-ENV:Envelope>  
    ```  
  
2.  <span data-ttu-id="b2795-137">プロバイダーからの SOAP 応答メッセージには、XMLA ヘッダータグを使用して、リターンヘッダー領域にセッション ID が含まれてい \<SessionId> ます。</span><span class="sxs-lookup"><span data-stu-id="b2795-137">The SOAP response message from the provider includes the session ID in the return header area, using the XMLA header tag \<SessionId>.</span></span>  
  
    ```  
    <SOAP-ENV:Header>  
       <XA:Session  
          xmlns:XA="urn:schemas-microsoft-com:xml-analysis"  
          SessionId="581"/>  
    </SOAP-ENV:Header>  
    ```  
  
3.  <span data-ttu-id="b2795-138">セッションのメソッド呼び出しごとに、プロバイダーから返されたセッション ID を含む Session ヘッダーを追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b2795-138">For each method call in the session, the Session header must be added, containing the session ID returned from the provider.</span></span>  
  
    ```  
    <SOAP-ENV:Header>  
       <XA:Session  
          xmlns:XA="urn:schemas-microsoft-com:xml-analysis"  
          mustUnderstand="1"  
          SessionId="581"/>  
    </SOAP-ENV:Header>  
    ```  
  
4.  <span data-ttu-id="b2795-139">セッションが完了すると、 \<EndSession> 関連するセッション ID 値を含むタグが使用されます。</span><span class="sxs-lookup"><span data-stu-id="b2795-139">When the session is complete, the \<EndSession> tag is used, containing the related session ID value.</span></span>  
  
    ```  
    <SOAP-ENV:Header>  
       <XA:EndSession  
          xmlns:XA="urn:schemas-microsoft-com:xml-analysis"  
          xsi:type="xsd:int"  
          mustUnderstand="1"  
          SessionId="581"/>  
    </SOAP-ENV:Header>  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="b2795-140">参照</span><span class="sxs-lookup"><span data-stu-id="b2795-140">See Also</span></span>  
 [<span data-ttu-id="b2795-141">Analysis Services での XMLA による開発</span><span class="sxs-lookup"><span data-stu-id="b2795-141">Developing with XMLA in Analysis Services</span></span>](developing-with-xmla-in-analysis-services.md)  
  
  
