---
title: セキュリティで保護された Web サービス メソッドの使用 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- SOAP [Reporting Services], secure connections
- Web service [Reporting Services], SOAP
- Report Server Web service, SOAP
- XML Web service [Reporting Services], SOAP
ms.assetid: 87329299-c2ea-4517-9148-d855726768a9
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: e88a164602f9bbe6ad42c3897285a484cac94466
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739217"
---
# <a name="using-secure-web-service-methods"></a><span data-ttu-id="8bc3f-102">セキュリティで保護された Web サービス メソッドの使用</span><span class="sxs-lookup"><span data-stu-id="8bc3f-102">Using Secure Web Service Methods</span></span>
  <span data-ttu-id="8bc3f-103">特定のレポート サーバー Web サービスを呼び出す場合に、セキュリティによる接続の保護が必要なことがあります。</span><span class="sxs-lookup"><span data-stu-id="8bc3f-103">Certain Report Server Web service methods may require a secure connection when you invoke them.</span></span> <span data-ttu-id="8bc3f-104">セキュリティで保護された接続を必要とするメソッドは、RSReportServer.config ファイルの `SecureConnectionLevel` 設定で決まります。</span><span class="sxs-lookup"><span data-stu-id="8bc3f-104">The methods that require a secure connection are determined by the `SecureConnectionLevel` setting in the RSReportServer.config file.</span></span> <span data-ttu-id="8bc3f-105">有効な設定値は 0 以上の整数値です。</span><span class="sxs-lookup"><span data-stu-id="8bc3f-105">The value of the setting is an integer value with a valid range of 0 and higher.</span></span> <span data-ttu-id="8bc3f-106">次の表では、これらの値を説明します。</span><span class="sxs-lookup"><span data-stu-id="8bc3f-106">The following table describes these values.</span></span>  
  
|<span data-ttu-id="8bc3f-107">Level</span><span class="sxs-lookup"><span data-stu-id="8bc3f-107">Level</span></span>|<span data-ttu-id="8bc3f-108">説明</span><span class="sxs-lookup"><span data-stu-id="8bc3f-108">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="8bc3f-109">**0**</span><span class="sxs-lookup"><span data-stu-id="8bc3f-109">**0**</span></span>|<span data-ttu-id="8bc3f-110">セキュリティで保護されません。</span><span class="sxs-lookup"><span data-stu-id="8bc3f-110">Not secure.</span></span> <span data-ttu-id="8bc3f-111">Reporting Services SOAP API への呼び出しに対して、セキュリティで保護された接続は不要です。</span><span class="sxs-lookup"><span data-stu-id="8bc3f-111">Calls made to the Reporting Services SOAP API do not require a secure connection.</span></span>|  
|<span data-ttu-id="8bc3f-112">**0** より大きい。</span><span class="sxs-lookup"><span data-stu-id="8bc3f-112">Greater than **0**</span></span>|<span data-ttu-id="8bc3f-113">セキュリティで保護されます。</span><span class="sxs-lookup"><span data-stu-id="8bc3f-113">Secure.</span></span> <span data-ttu-id="8bc3f-114">Reporting Services SOAP API へのすべての呼び出しに対して、セキュリティで保護された接続が必要です。</span><span class="sxs-lookup"><span data-stu-id="8bc3f-114">All calls made to the Reporting Services SOAP API require a secure connection.</span></span>|  
  
 <span data-ttu-id="8bc3f-115">Web サービスの <xref:ReportExecution2005.ReportExecutionService.ListSecureMethods%2A> メソッドを使用して、レポート サーバーの現在の構成に基づいて、セキュリティで保護された接続を必要とする Web サービス メソッドの一覧を返すことができます。</span><span class="sxs-lookup"><span data-stu-id="8bc3f-115">You can use the <xref:ReportExecution2005.ReportExecutionService.ListSecureMethods%2A> method of the Web service to return a list of Web service methods that require a secure connection according to the current configuration of the report server.</span></span> <span data-ttu-id="8bc3f-116">SSL を使用する場合は、<xref:ReportExecution2005.ReportExecutionService.ListSecureMethods%2A> によって返されたメソッドの一覧を評価し、呼び出すメソッドに応じて Web サービス URI のスキーマ名を "https" または "http" に変更します。</span><span class="sxs-lookup"><span data-stu-id="8bc3f-116">In an SSL scenario, you should evaluate the list of methods that are returned by <xref:ReportExecution2005.ReportExecutionService.ListSecureMethods%2A> and change the scheme name of the Web service URI to "https" or "http" depending on the method being called.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8bc3f-117">参照</span><span class="sxs-lookup"><span data-stu-id="8bc3f-117">See Also</span></span>  
 <span data-ttu-id="8bc3f-118">[Web サービスと .NET Framework を使用してのアプリケーションの構築](building-applications-using-the-web-service-and-the-net-framework.md) </span><span class="sxs-lookup"><span data-stu-id="8bc3f-118">[Building Applications Using the Web Service and the .NET Framework](building-applications-using-the-web-service-and-the-net-framework.md) </span></span>  
 [<span data-ttu-id="8bc3f-119">レポート サーバー web サービス</span><span class="sxs-lookup"><span data-stu-id="8bc3f-119">Report Server Web Service</span></span>](../report-server-web-service.md)  
  
  
