---
title: Web サービス メソッドの引数の指定 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- Report Server Web service, methods
- Web service [Reporting Services], methods
- methods [Reporting Services], arguments
- XML Web service [Reporting Services], methods
ms.assetid: f7b9ca05-fc4c-4b30-8e5d-172dd0f4a832
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 3ef5188934628589751fe92d1839da0efb265766
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739211"
---
# <a name="supplying-web-service-method-arguments"></a><span data-ttu-id="1e2c0-102">Web サービス メソッドの引数の指定</span><span class="sxs-lookup"><span data-stu-id="1e2c0-102">Supplying Web Service Method Arguments</span></span>
  <span data-ttu-id="1e2c0-103">レポート サーバー Web サービスのメソッドは、SOAP を使用し、HTTP 経由で特定の URL のサービスに対して要求を送信します。</span><span class="sxs-lookup"><span data-stu-id="1e2c0-103">A Report Server Web service method sends a request to the service at a given URL using SOAP over HTTP.</span></span> <span data-ttu-id="1e2c0-104">サービスでは、要求を受信し、処理した後、応答を返します。</span><span class="sxs-lookup"><span data-stu-id="1e2c0-104">The service receives the request, processes it, and then returns a response.</span></span> <span data-ttu-id="1e2c0-105">これらの要求と応答は XML ドキュメント形式です。</span><span class="sxs-lookup"><span data-stu-id="1e2c0-105">These requests and responses are in the form of XML documents.</span></span>  
  
## <a name="optional-parameters"></a><span data-ttu-id="1e2c0-106">省略可能のパラメーター</span><span class="sxs-lookup"><span data-stu-id="1e2c0-106">Optional Parameters</span></span>  
 <span data-ttu-id="1e2c0-107">場合によっては、Web サービス メソッドに省略可能な入力パラメーターがあります。</span><span class="sxs-lookup"><span data-stu-id="1e2c0-107">In some cases, a Web service method can have optional input parameters.</span></span> <span data-ttu-id="1e2c0-108">Web サービス メソッドの入力パラメーターが省略可能である場合でも、そのパラメーターを含め、パラメーター値を `null` ([!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] の場合は `Nothing`) に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1e2c0-108">Even if an input parameter for a Web service method is optional, you must still include it and set the parameter value to `null` (`Nothing` in [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]).</span></span> <span data-ttu-id="1e2c0-109">パラメーター値を `null` に設定すると、SOAP 要求でそのパラメーターの要素値は `null` に設定されます。</span><span class="sxs-lookup"><span data-stu-id="1e2c0-109">Setting a parameter value to `null` sets the element value for that parameter in the SOAP request to `null`.</span></span>  
  
 <span data-ttu-id="1e2c0-110">次の例では、<xref:ReportService2010.ReportingService2010.CreateFolder%2A> メソッドを使用して、Sales フォルダーに Product Sales という新しいフォルダーを作成します。</span><span class="sxs-lookup"><span data-stu-id="1e2c0-110">The following example uses the <xref:ReportService2010.ReportingService2010.CreateFolder%2A> method to create a new folder named Product Sales in the Sales folder.</span></span> <span data-ttu-id="1e2c0-111">フォルダー プロパティに `null` 値を指定することで、フォルダーにユーザー固有のプロパティは指定されません。</span><span class="sxs-lookup"><span data-stu-id="1e2c0-111">By supplying a `null` value for the folder properties, no user-specific properties are supplied for the folder:</span></span>  
  
```  
// C#  
rs.CreateFolder("Product Sales", "/Sales", null);  
```  
  
## <a name="complex-data-types"></a><span data-ttu-id="1e2c0-112">複合データ型</span><span class="sxs-lookup"><span data-stu-id="1e2c0-112">Complex Data Types</span></span>  
 <span data-ttu-id="1e2c0-113">レポート サーバー Web サービスのコア クラスは <xref:ReportService2010.ReportingService2010> です。このクラスは、プロキシ クラスの SOAP 操作または Web メソッドを呼び出すときに使用します。</span><span class="sxs-lookup"><span data-stu-id="1e2c0-113">The core class of the Report Server Web service is <xref:ReportService2010.ReportingService2010>, which you use to invoke the SOAP operations or Web methods of the proxy class.</span></span> <span data-ttu-id="1e2c0-114">このクラスとメソッドをサポートするため、[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] には、Web サービス メソッドの入出力パラメーターに固有であるユーザー定義の複合データ型が含まれます。</span><span class="sxs-lookup"><span data-stu-id="1e2c0-114">To support this class and its methods, [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] includes user-defined, complex data types that are specific to the input and output parameters of the Web service methods.</span></span> <span data-ttu-id="1e2c0-115">これらの複合データ型は、環境で開発するときに使用できる、生成されるプロキシクラスの一部です [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="1e2c0-115">These complex data types are part of the generated proxy class, which you can use when developing in the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] environment.</span></span>  
  
 <span data-ttu-id="1e2c0-116">プロキシ クラスを生成すると、WSDL ファイルに定義された複合データ型はプロキシのクラスによって表されます。このクラスには、複合データ型のさまざまな SOAP 要素に対応するプロパティが入っています。</span><span class="sxs-lookup"><span data-stu-id="1e2c0-116">When you generate a proxy class, the complex data types that are defined in the WSDL file are represented by the classes of the proxy, which include properties that correspond to the various SOAP elements of the complex data types.</span></span> <span data-ttu-id="1e2c0-117">一連の複合データ型は、コードで列挙できるオブジェクトの配列になります。</span><span class="sxs-lookup"><span data-stu-id="1e2c0-117">Sequences of these data types become arrays of objects that you can enumerate through in your code.</span></span> <span data-ttu-id="1e2c0-118">したがって、SOAP メッセージで送信された XML 構造を直接扱う必要がなくなります。</span><span class="sxs-lookup"><span data-stu-id="1e2c0-118">This eliminates the need to work directly with the XML structures sent in SOAP messages.</span></span> <span data-ttu-id="1e2c0-119">[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] では、自動的に変換が行われます。</span><span class="sxs-lookup"><span data-stu-id="1e2c0-119">The [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] handles that translation for you.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e2c0-120">参照</span><span class="sxs-lookup"><span data-stu-id="1e2c0-120">See Also</span></span>  
 <span data-ttu-id="1e2c0-121">[Web サービスと .NET Framework を使用してのアプリケーションの構築](building-applications-using-the-web-service-and-the-net-framework.md) </span><span class="sxs-lookup"><span data-stu-id="1e2c0-121">[Building Applications Using the Web Service and the .NET Framework](building-applications-using-the-web-service-and-the-net-framework.md) </span></span>  
 <span data-ttu-id="1e2c0-122">[レポート サーバー Web サービス](../report-server-web-service.md) </span><span class="sxs-lookup"><span data-stu-id="1e2c0-122">[Report Server Web Service](../report-server-web-service.md) </span></span>  
 [<span data-ttu-id="1e2c0-123">テクニカル リファレンス (SSRS)</span><span class="sxs-lookup"><span data-stu-id="1e2c0-123">Technical Reference &#40;SSRS&#41;</span></span>](../../technical-reference-ssrs.md)  
  
  
