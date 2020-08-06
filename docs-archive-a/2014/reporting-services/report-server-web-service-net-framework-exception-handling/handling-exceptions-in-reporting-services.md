---
title: Reporting Services での例外を処理 | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- SOAP [Reporting Services], exceptions
- .NET Framework [Reporting Services]
- exceptions [Reporting Services], about exception handling
- SoapException object
ms.assetid: 1a443432-2db5-48c5-bc29-433b4688082f
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 1d887853b475f7b4d673d7b04343ae9bc71644d3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87719539"
---
# <a name="handling-exceptions-in-reporting-services"></a><span data-ttu-id="60f44-102">Reporting Services の例外の処理</span><span class="sxs-lookup"><span data-stu-id="60f44-102">Handling Exceptions in Reporting Services</span></span>
  <span data-ttu-id="60f44-103">Reporting Services SOAP API クライアント要求を完了できない場合は、レポート サーバーが予期した呼び出しの結果ではなくエラーを返します。</span><span class="sxs-lookup"><span data-stu-id="60f44-103">When a Reporting Services SOAP API client request cannot be completed, the report server returns an error rather than the expected results of the call.</span></span> <span data-ttu-id="60f44-104">呼び出しを完了できない場合は、レポート サーバー Web サービスのエラーが SOAP **Fault** XML 要素として返されます。</span><span class="sxs-lookup"><span data-stu-id="60f44-104">When a call cannot complete, an error for the Report Server Web service is returned as a SOAP **Fault** XML element.</span></span> <span data-ttu-id="60f44-105">エラー解消の鍵となる要素は **detail** 要素です。この要素には、レポート サーバーが提供するすべてのエラー情報に加えて、Web サービス エラー情報も含まれています。</span><span class="sxs-lookup"><span data-stu-id="60f44-105">The key descriptive element of the fault is the **detail** element, which includes all of the error information provided by the report server as well as any additional Web service error information.</span></span> <span data-ttu-id="60f44-106">**detail** 要素の中の最重要情報は、レポート サーバー エラー コードです。</span><span class="sxs-lookup"><span data-stu-id="60f44-106">The key information in the **detail** element is the report server error code.</span></span> <span data-ttu-id="60f44-107">メッセージとエラー コードから、アプリケーションで次にとるべき適切な処理を判断することができます。</span><span class="sxs-lookup"><span data-stu-id="60f44-107">Based on the message and error code, you can determine the next appropriate action to take in your applications.</span></span> <span data-ttu-id="60f44-108">SOAP エラーの詳細については、W3C (World Wide Web Consortium) の Web サイト (http://www.w3.org/TR/SOAP) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="60f44-108">For more information about SOAP faults, see the World Wide Web Consortium (W3C) Web site at http://www.w3.org/TR/SOAP.</span></span>  
  
## <a name="soap-faults-and-the-net-framework"></a><span data-ttu-id="60f44-109">SOAP のエラーと .NET Framework</span><span class="sxs-lookup"><span data-stu-id="60f44-109">SOAP Faults and the .NET Framework</span></span>  
 <span data-ttu-id="60f44-110">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] では、Web サービスへのクライアント要求でエラーが発生した場合に、レポート サーバーが **SoapException** オブジェクトをスローすることにより Web サービスを呼び出すクライアント コードにエラーが通知されます。</span><span class="sxs-lookup"><span data-stu-id="60f44-110">In the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)], if an error occurs in a client request to the Web service, the report server communicates the error to the client code that calls the Web service by throwing a **SoapException** object.</span></span> <span data-ttu-id="60f44-111">**SoapException** は SOAP エラーに含まれる情報をラップします。</span><span class="sxs-lookup"><span data-stu-id="60f44-111">The **SoapException** wraps the information contained in a SOAP fault.</span></span> <span data-ttu-id="60f44-112">**SoapException** の **Detail** プロパティは、SOAP エラーの **detail** 要素にマップされます。</span><span class="sxs-lookup"><span data-stu-id="60f44-112">The **Detail** property of the **SoapException** maps to the **detail** element in the SOAP fault.</span></span> <span data-ttu-id="60f44-113">アプリケーションは **SoapException** オブジェクトを try ブロックまたは catch ブロックと共にキャッチし、**SoapException** の **Detail** プロパティを使用して適切な処理を行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="60f44-113">Applications should catch the **SoapException** object with a try/catch block and use the **Detail** property of the **SoapException** to take appropriate action.</span></span> <span data-ttu-id="60f44-114">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] の **SoapException** クラスと **Detail** プロパティの詳細については、「[Reporting Services SoapException クラス](soapexception-class/reporting-services-soapexception-class.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="60f44-114">For more information about the **SoapException** class and the **Detail** property in [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], see [Reporting Services SoapException Class](soapexception-class/reporting-services-soapexception-class.md).</span></span> <span data-ttu-id="60f44-115">**SoapException** クラスの詳細については、[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK ドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="60f44-115">For more information about the **SoapException** class, see the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK documentation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60f44-116">参照</span><span class="sxs-lookup"><span data-stu-id="60f44-116">See Also</span></span>  
 <span data-ttu-id="60f44-117">[Detail プロパティ](soapexception-class/detail-property.md) </span><span class="sxs-lookup"><span data-stu-id="60f44-117">[Detail Property](soapexception-class/detail-property.md) </span></span>  
 <span data-ttu-id="60f44-118">[Reporting Services における例外処理の概要](introducing-exception-handling-in-reporting-services.md) </span><span class="sxs-lookup"><span data-stu-id="60f44-118">[Introducing Exception Handling in Reporting Services](introducing-exception-handling-in-reporting-services.md) </span></span>  
 [<span data-ttu-id="60f44-119">Reporting Services SoapException クラス</span><span class="sxs-lookup"><span data-stu-id="60f44-119">Reporting Services SoapException Class</span></span>](soapexception-class/reporting-services-soapexception-class.md)  
  
  
