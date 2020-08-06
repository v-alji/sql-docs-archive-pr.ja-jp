---
title: Reporting Services の SOAP ヘッダーの使用 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- Web service [Reporting Services], SOAP
- Report Server Web service, SOAP
- SOAP headers [Reporting Services]
- SOAP [Reporting Services], headers
- XML Web service [Reporting Services], SOAP
ms.assetid: 306d2c06-a25a-40f8-8a35-13dd32e8841e
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: f48be183398d4d441b5781c9f9467178c3011e32
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87717372"
---
# <a name="using-reporting-services-soap-headers"></a><span data-ttu-id="51474-102">Reporting Services の SOAP ヘッダーの使用</span><span class="sxs-lookup"><span data-stu-id="51474-102">Using Reporting Services SOAP Headers</span></span>
  <span data-ttu-id="51474-103">SOAP を使用した Web サービス メソッドとの通信では、標準形式に従います。</span><span class="sxs-lookup"><span data-stu-id="51474-103">Communication with a Web service method using SOAP follows a standard format.</span></span> <span data-ttu-id="51474-104">この標準形式の一部は、XML ドキュメントでエンコードされるデータです。</span><span class="sxs-lookup"><span data-stu-id="51474-104">Part of this format is the data that is encoded in an XML document.</span></span> <span data-ttu-id="51474-105">XML ドキュメントは、ルート **Envelope** 要素で構成され、さらにその要素は必須の **Body** 要素および省略可能な **Header** 要素で構成されます。</span><span class="sxs-lookup"><span data-stu-id="51474-105">The XML document consists of a root **Envelope** element, which in turn consists of a required **Body** element and an optional **Header** element.</span></span> <span data-ttu-id="51474-106">**Body** 要素には、メッセージ固有のデータが含まれます。</span><span class="sxs-lookup"><span data-stu-id="51474-106">The **Body** element contains the data specific to the message.</span></span> <span data-ttu-id="51474-107">省略可能な **Header** 要素には、特定のメッセージに直接関連しない追加情報を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="51474-107">The optional **Header** element can contain additional information not directly related to the particular message.</span></span> <span data-ttu-id="51474-108">**Header** 要素の各子要素は、SOAP ヘッダーと呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="51474-108">Each child element of the **Header** element is called a SOAP header.</span></span>  
  
 <span data-ttu-id="51474-109">SOAP ヘッダーには、メッセージに関連するデータを含めることができますが、一般的には Web サーバー内のインフラストラクチャによって処理される情報が含まれます。</span><span class="sxs-lookup"><span data-stu-id="51474-109">Although the SOAP headers can contain data related to the message, they typically contain information processed by the Web server infrastructure.</span></span>  
  
 <span data-ttu-id="51474-110">レポート サーバー Web サービスでは、SOAP ヘッダーで使用される複数のクラス、つまり <xref:ReportService2005.BatchHeader>、<xref:ReportService2010.ItemNamespaceHeader>、<xref:ReportService2010.ServerInfoHeader>、<xref:ReportService2010.TrustedUserHeader>、および <xref:ReportExecution2005.ExecutionHeader> を定義します。</span><span class="sxs-lookup"><span data-stu-id="51474-110">The Report Server Web services define several classes for use in the SOAP header: <xref:ReportService2005.BatchHeader>, <xref:ReportService2010.ItemNamespaceHeader>, <xref:ReportService2010.ServerInfoHeader>, <xref:ReportService2010.TrustedUserHeader>, and <xref:ReportExecution2005.ExecutionHeader>.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="51474-111">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="51474-111">In This Section</span></span>  
  
|<span data-ttu-id="51474-112">トピック</span><span class="sxs-lookup"><span data-stu-id="51474-112">Topic</span></span>|<span data-ttu-id="51474-113">説明</span><span class="sxs-lookup"><span data-stu-id="51474-113">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="51474-114">メソッドのバッチ処理</span><span class="sxs-lookup"><span data-stu-id="51474-114">Batching Methods</span></span>](batching-methods.md)|<span data-ttu-id="51474-115"><xref:ReportService2005.BatchHeader> を使用して、複数の操作を 1 つのトランザクションにまとめる方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="51474-115">Describes how to batch multiple operations into a single transaction using <xref:ReportService2005.BatchHeader>.</span></span>|  
|[<span data-ttu-id="51474-116">実行状態の識別</span><span class="sxs-lookup"><span data-stu-id="51474-116">Identifying Execution State</span></span>](identifying-execution-state.md)|<span data-ttu-id="51474-117">**Session Header** を使って、[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] でセッション状態を管理する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="51474-117">Describes how to manage session state in [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] using **SessionHeader**.</span></span>|  
|[<span data-ttu-id="51474-118">GetProperties メソッドのアイテム名前空間の設定</span><span class="sxs-lookup"><span data-stu-id="51474-118">Setting the Item Namespace for the GetProperties Method</span></span>](setting-the-item-namespace-for-the-getproperties-method.md)|<span data-ttu-id="51474-119"><xref:ReportService2010.ReportingService2010.GetProperties%2A> メソッドおよび <xref:ReportService2010.ItemNamespaceHeader> SOAP ヘッダーを使用することによって、アイテムのパスまたは ID に基づいたプロパティを取得する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="51474-119">Describes how to retrieve properties based on either the path or the ID of an item by using the <xref:ReportService2010.ReportingService2010.GetProperties%2A> method and the <xref:ReportService2010.ItemNamespaceHeader> SOAP header.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="51474-120">参照</span><span class="sxs-lookup"><span data-stu-id="51474-120">See Also</span></span>  
 <span data-ttu-id="51474-121">[Web サービスと .NET Framework を使用してのアプリケーションの構築](../report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md) </span><span class="sxs-lookup"><span data-stu-id="51474-121">[Building Applications Using the Web Service and the .NET Framework](../report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md) </span></span>  
 [<span data-ttu-id="51474-122">テクニカル リファレンス (SSRS)</span><span class="sxs-lookup"><span data-stu-id="51474-122">Technical Reference &#40;SSRS&#41;</span></span>](../technical-reference-ssrs.md)  
  
  
