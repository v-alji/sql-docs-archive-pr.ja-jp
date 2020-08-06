---
title: Reporting Services 例外処理のベスト プラクティス | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- exceptions [Reporting Services], best practices
ms.assetid: 72fecf28-f02e-4338-b50f-0b21f520302d
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 2e0561c19fbd3e709a0440a55f023f938eabf692
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639898"
---
# <a name="best-practices-for-reporting-services-exception-handling"></a><span data-ttu-id="c1eee-102">Reporting Services 例外処理のベスト プラクティス</span><span class="sxs-lookup"><span data-stu-id="c1eee-102">Best Practices for Reporting Services Exception Handling</span></span>
  <span data-ttu-id="c1eee-103">[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] アプリケーションを開発する場合、例外の発生を排除または削減するための方法がいくつかあります。</span><span class="sxs-lookup"><span data-stu-id="c1eee-103">When developing [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] applications, there are several methodologies you can use to eliminate or reduce the occurrence of exceptions.</span></span> <span data-ttu-id="c1eee-104">例外が発生した場合に、明確かつ簡潔なエラー メッセージをユーザーに提供し、アプリケーションの異常終了を防止するために十分な例外処理を追加してください。</span><span class="sxs-lookup"><span data-stu-id="c1eee-104">When exceptions do occur, provide clear and concise error messages to the user, and add adequate exception handling to prevent your applications from ending unexpectedly.</span></span>  
  
 <span data-ttu-id="c1eee-105">要求をレポート サーバー Web サービスに送信するアプリケーションは、次のことを実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c1eee-105">An application that sends requests to the Report Server Web service should do the following:</span></span>  
  
-   <span data-ttu-id="c1eee-106">無効な要求をできる限り多く防ぐことによって、例外の発生を回避します。</span><span class="sxs-lookup"><span data-stu-id="c1eee-106">Avoid causing exceptions by preventing as many invalid requests as possible.</span></span>  
  
-   <span data-ttu-id="c1eee-107">例外をキャッチし、可能な場合は特定のエラー処理コードを提供します。</span><span class="sxs-lookup"><span data-stu-id="c1eee-107">Catch exceptions and provide specific error-handling code whenever possible.</span></span>  
  
-   <span data-ttu-id="c1eee-108">例外をスローしないエラーを処理します。</span><span class="sxs-lookup"><span data-stu-id="c1eee-108">Deal with error cases that do not throw exceptions.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c1eee-109">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="c1eee-109">In This Section</span></span>  
  
|<span data-ttu-id="c1eee-110">トピック</span><span class="sxs-lookup"><span data-stu-id="c1eee-110">Topic</span></span>|<span data-ttu-id="c1eee-111">説明</span><span class="sxs-lookup"><span data-stu-id="c1eee-111">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="c1eee-112">無効な要求の回避</span><span class="sxs-lookup"><span data-stu-id="c1eee-112">Preventing Invalid Requests</span></span>](preventing-invalid-requests.md)|<span data-ttu-id="c1eee-113">無効な要求がレポート サーバーに送信されるのを回避する技術について説明します。</span><span class="sxs-lookup"><span data-stu-id="c1eee-113">Describes techniques for preventing requests that are not valid from being sent to the report server.</span></span>|  
|[<span data-ttu-id="c1eee-114">Try ブロックと Catch ブロックの使用</span><span class="sxs-lookup"><span data-stu-id="c1eee-114">Using Try and Catch Blocks</span></span>](using-try-and-catch-blocks.md)|<span data-ttu-id="c1eee-115">try ブロックと catch ブロックを使用して、アプリケーションの信頼性を高める方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="c1eee-115">Describes how to further enhance the reliability of your application with try/catch blocks.</span></span>|  
|[<span data-ttu-id="c1eee-116">例外が発生しない警告および状況の処理</span><span class="sxs-lookup"><span data-stu-id="c1eee-116">Handling Warnings and Cases That Do Not Cause Exceptions</span></span>](handling-warnings-and-cases-that-do-not-cause-exceptions.md)|<span data-ttu-id="c1eee-117">[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] によってスローされない例外となるエラーの処理方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="c1eee-117">Explains how to handle errors that do not result in an exception being thrown by [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].</span></span>|  
|[<span data-ttu-id="c1eee-118">Detail プロパティを使用したエラー処理</span><span class="sxs-lookup"><span data-stu-id="c1eee-118">Using the Detail Property to Handle Specific Errors</span></span>](using-the-detail-property-to-handle-specific-errors.md)|<span data-ttu-id="c1eee-119">**SoapException** オブジェクトの **Detail** プロパティを使用して、特定のエラーをプログラムによって処理する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="c1eee-119">Explains how to programmatically handle specific errors by using the **Detail** property of the **SoapException** object.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c1eee-120">参照</span><span class="sxs-lookup"><span data-stu-id="c1eee-120">See Also</span></span>  
 <span data-ttu-id="c1eee-121">[Detail プロパティ](../soapexception-class/detail-property.md) </span><span class="sxs-lookup"><span data-stu-id="c1eee-121">[Detail Property](../soapexception-class/detail-property.md) </span></span>  
 <span data-ttu-id="c1eee-122">[Reporting Services における例外処理の概要](../introducing-exception-handling-in-reporting-services.md) </span><span class="sxs-lookup"><span data-stu-id="c1eee-122">[Introducing Exception Handling in Reporting Services](../introducing-exception-handling-in-reporting-services.md) </span></span>  
 [<span data-ttu-id="c1eee-123">Reporting Services SoapException クラス</span><span class="sxs-lookup"><span data-stu-id="c1eee-123">Reporting Services SoapException Class</span></span>](../soapexception-class/reporting-services-soapexception-class.md)  
  
  
