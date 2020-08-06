---
title: Reporting Services における例外処理の概要 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- Web service [Reporting Services], exception handling
- errors [Reporting Services]
- exceptions [Reporting Services]
- Report Server Web service, exception handling
- XML Web service [Reporting Services], exception handling
ms.assetid: 54381870-ce67-482b-aa83-6a838cdbf9b9
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 091b1f40d293515617e369b750a5f18dfe12951b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87715101"
---
# <a name="introducing-exception-handling-in-reporting-services"></a><span data-ttu-id="c648f-102">Reporting Services における例外処理の概要</span><span class="sxs-lookup"><span data-stu-id="c648f-102">Introducing Exception Handling in Reporting Services</span></span>
  <span data-ttu-id="c648f-103">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] アプリケーションが要求をレポート サーバー Web サービスに送信し、サービスが要求を処理できない場合、サービスは SOAP 例外をクライアントに返します。</span><span class="sxs-lookup"><span data-stu-id="c648f-103">If your [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] application sends a request to the Report Server Web service that the service is unable to process, the service returns a SOAP exception to the client.</span></span> <span data-ttu-id="c648f-104">レポート サーバー Web サービスによってスローされた例外の処理は、開発するアプリケーションの重要な部分です。エラーが発生した場合にユーザーに有益な情報を返すことができるからです。</span><span class="sxs-lookup"><span data-stu-id="c648f-104">Handling exceptions thrown by the Report Server Web service is an important part of the applications that you develop because you can return useful information to users when errors occur.</span></span>  
  
 <span data-ttu-id="c648f-105">ここでは、例外の処理、無効なユーザー入力の回避、およびユーザーへの有意義なエラー情報の送信について説明します。</span><span class="sxs-lookup"><span data-stu-id="c648f-105">This section contains specific information about handling exceptions, preventing user input that is not valid, and returning meaningful error information to users.</span></span> <span data-ttu-id="c648f-106">例外処理の一般的な情報については、SDK ドキュメントの「例外の処理とスロー」を参照してください [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="c648f-106">For general information about exception handling, see "Handling and Throwing Exceptions" in the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK documentation.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c648f-107">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="c648f-107">In This Section</span></span>  
  
|<span data-ttu-id="c648f-108">トピック</span><span class="sxs-lookup"><span data-stu-id="c648f-108">Topic</span></span>|<span data-ttu-id="c648f-109">説明</span><span class="sxs-lookup"><span data-stu-id="c648f-109">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="c648f-110">Reporting Services の例外の処理</span><span class="sxs-lookup"><span data-stu-id="c648f-110">Handling Exceptions in Reporting Services</span></span>](handling-exceptions-in-reporting-services.md)|<span data-ttu-id="c648f-111">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] における例外および Web サービスからエラーを返すときの SOAP の役割について説明します。</span><span class="sxs-lookup"><span data-stu-id="c648f-111">Provides an overview of exceptions in [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] and the role of SOAP in returning errors from a Web service.</span></span>|  
|[<span data-ttu-id="c648f-112">Reporting Services 例外処理のベスト プラクティス</span><span class="sxs-lookup"><span data-stu-id="c648f-112">Best Practices for Reporting Services Exception Handling</span></span>](best-practices/best-practices-for-reporting-services-exception-handling.md)|<span data-ttu-id="c648f-113">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] での例外処理に関する推奨事項が記載されています。</span><span class="sxs-lookup"><span data-stu-id="c648f-113">Provides recommendations on how to handle exceptions in [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span>|  
|[<span data-ttu-id="c648f-114">Reporting Services SoapException クラス</span><span class="sxs-lookup"><span data-stu-id="c648f-114">Reporting Services SoapException Class</span></span>](soapexception-class/reporting-services-soapexception-class.md)|<span data-ttu-id="c648f-115">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] の **SoapException** クラスについて説明します。</span><span class="sxs-lookup"><span data-stu-id="c648f-115">Describes the **SoapException** class in [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c648f-116">参照</span><span class="sxs-lookup"><span data-stu-id="c648f-116">See Also</span></span>  
 [<span data-ttu-id="c648f-117">Web サービスと .NET Framework を使用してのアプリケーションの構築</span><span class="sxs-lookup"><span data-stu-id="c648f-117">Building Applications Using the Web Service and the .NET Framework</span></span>](../report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md)  
  
  
