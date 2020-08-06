---
title: クライアント側とサーバー側の XML 書式設定のアーキテクチャ (SQLXML 4.0) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- providers [SQLXML], XML formatting architecture
- SQLOLEDB provider
- client-side XML formatting
- data providers [SQLXML], XML formatting architecture
- SQLNCLI, XML
- server-side XML formatting
- SQL Server Native Client, XML
- SQLXMLOLEDB Provider, XML formatting architecture
ms.assetid: 52440d9e-89fd-4c15-a008-a1ea99f41387
author: rothja
ms.author: jroth
ms.openlocfilehash: ae1a9c60a7a7966f4eff2a08b4557487f5aec58c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642678"
---
# <a name="architecture-of-client-side-and-server-side-xml-formatting-sqlxml-40"></a><span data-ttu-id="3c0e2-102">クライアント側とサーバー側の XML 書式設定のアーキテクチャ (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="3c0e2-102">Architecture of Client-side and Server-side XML Formatting (SQLXML 4.0)</span></span>
  <span data-ttu-id="3c0e2-103">次の図は、サーバー側の XML 書式設定のアーキテクチャです。</span><span class="sxs-lookup"><span data-stu-id="3c0e2-103">The following illustration shows the architecture of XML formatting on the server side.</span></span>  
  
 <span data-ttu-id="3c0e2-104">![サーバー側の XML 処理のアーキテクチャ](../../../database-engine/dev-guide/media/serversidexml.gif "サーバー側の XML 処理のアーキテクチャ")</span><span class="sxs-lookup"><span data-stu-id="3c0e2-104">![Architecture of XML formatting on the server side.](../../../database-engine/dev-guide/media/serversidexml.gif "Architecture of XML formatting on the server side.")</span></span>  
  
 <span data-ttu-id="3c0e2-105">この例では、クライアント側で指定されたコマンドがサーバーに送信されます。</span><span class="sxs-lookup"><span data-stu-id="3c0e2-105">In this example, the command that is specified on the client is sent to the server.</span></span> <span data-ttu-id="3c0e2-106">サーバーでは XML ドキュメントが生成され、それがクライアントに返されます。</span><span class="sxs-lookup"><span data-stu-id="3c0e2-106">The server produces an XML document and returns it to the client.</span></span> <span data-ttu-id="3c0e2-107">この場合、サーバーにはのインスタンスがあり [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="3c0e2-107">In this case, the server has an instance of [!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="3c0e2-108">サーバー側の XML 書式設定では、SQLXMLOLEDB プロバイダーまたは SQLOLEDB プロバイダーのいずれかを使用できます。</span><span class="sxs-lookup"><span data-stu-id="3c0e2-108">With server-side XML formatting, you can use either the SQLXMLOLEDB provider or the SQLOLEDB provider.</span></span>  <span data-ttu-id="3c0e2-109">SQLXMLOLEDB プロバイダーでは Sqlxml4.dll が使用されますが、これは SQLXML 4.0 に含まれています。</span><span class="sxs-lookup"><span data-stu-id="3c0e2-109">The SQLXMLOLEDB provider uses Sqlxml4.dll, which is included in SQLXML 4.0.</span></span> <span data-ttu-id="3c0e2-110">SQLOLEDB プロバイダーを使用する場合、既定では Sqlxmlx.dll により SQLXML の機能が提供されます。この dll は [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows または Microsoft Data Access Components (MDAC) 2.6 以降に含まれています。</span><span class="sxs-lookup"><span data-stu-id="3c0e2-110">When you use the SQLOLEDB provider, by default you get the SQLXML functionality provided by Sqlxmlx.dll, which is included with [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows or in Microsoft Data Access Components (MDAC) 2.6 or later.</span></span> <span data-ttu-id="3c0e2-111">SQLOLEDB で Sqlxml4.dll を使用するには、SQLOLEDB 接続オブジェクトで SQLXML Version プロパティを "SQLXML. 4.0" に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3c0e2-111">To use Sqlxml4.dll with SQLOLEDB, you must set the SQLXML Version property to "SQLXML.4.0" on the SQLOLEDB Connection object.</span></span> <span data-ttu-id="3c0e2-112">いずれの場合も、サーバーでは XML ドキュメントが生成され、それがクライアントに送信されます。</span><span class="sxs-lookup"><span data-stu-id="3c0e2-112">In either case, the server produces the XML document and sends it to the client.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3c0e2-113">XPath クエリとアップデートグラムはクライアントで解析されます。</span><span class="sxs-lookup"><span data-stu-id="3c0e2-113">XPath queries and updategrams are parsed on the client.</span></span> <span data-ttu-id="3c0e2-114">SQLXML 4.0 の XPath テンプレートまたはアップデートグラム機能を使用するには、Sqlxml4.dll を使用します。</span><span class="sxs-lookup"><span data-stu-id="3c0e2-114">To get the XPath template or updategram functionality in SQLXML 4.0, use Sqlxml4.dll.</span></span>  
  
 <span data-ttu-id="3c0e2-115">次の図は、クライアント側の XML 書式設定のアーキテクチャです。</span><span class="sxs-lookup"><span data-stu-id="3c0e2-115">The following illustration shows the architecture of XML formatting on the client side.</span></span>  
  
 <span data-ttu-id="3c0e2-116">![クライアント側の XML 形式設定のアーキテクチャ](../../../database-engine/dev-guide/media/clientsidexml.gif "クライアント側の XML 形式設定のアーキテクチャ")</span><span class="sxs-lookup"><span data-stu-id="3c0e2-116">![Architecture of XML formatting on the client side.](../../../database-engine/dev-guide/media/clientsidexml.gif "Architecture of XML formatting on the client side.")</span></span>  
  
 <span data-ttu-id="3c0e2-117">この例では、クライアントで SQLXMLOLEDB プロバイダーが使用されます。</span><span class="sxs-lookup"><span data-stu-id="3c0e2-117">In this example, the client uses the SQLXMLOLEDB provider.</span></span> <span data-ttu-id="3c0e2-118">接続文字列では、Data Provider プロパティを SQLOLEDB に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3c0e2-118">In the connection string, the Data Provider property must be set to SQLOLEDB.</span></span> <span data-ttu-id="3c0e2-119">(これは SQLXML 4.0 で受け入れられる唯一の値です)。クライアントで実行されるコマンドは、サーバーに送信されます。</span><span class="sxs-lookup"><span data-stu-id="3c0e2-119">(This is the only value accepted in SQLXML 4.0.) The command that is executed on the client is sent to the server.</span></span> <span data-ttu-id="3c0e2-120">サーバーで生成された行セットがクライアントに送信されます。</span><span class="sxs-lookup"><span data-stu-id="3c0e2-120">The rowset that is generated on the server is sent to the client.</span></span> <span data-ttu-id="3c0e2-121">クライアントでは、行セットから XML ドキュメントの書式が設定されます。</span><span class="sxs-lookup"><span data-stu-id="3c0e2-121">The formatting of the XML document from the rowset is performed on the client.</span></span>  
  
 <span data-ttu-id="3c0e2-122">SQLXML 4.0 では、データ プロバイダーとして [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client (SQLNCLI11) または SQLOLEDB プロバイダーを使用できます。</span><span class="sxs-lookup"><span data-stu-id="3c0e2-122">In SQLXML 4.0, either the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client (SQLNCLI11) or the SQLOLEDB provider can be used as the data provider.</span></span> <span data-ttu-id="3c0e2-123">これらのプロバイダーでは、どのデータ ソースにもアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="3c0e2-123">You can potentially access any data source.</span></span> <span data-ttu-id="3c0e2-124">クエリで単一の行セットが返される限り、XML 変換はクライアント側で適用できます。</span><span class="sxs-lookup"><span data-stu-id="3c0e2-124">As long as the query returns a single rowset, the XML transformation can be applied on the client.</span></span>  
  
  
