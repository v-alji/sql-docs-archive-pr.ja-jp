---
title: ATOM デバイス情報設定 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: fe4a56a4-5552-423c-85c1-895e2e212fee
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: bdbac1500063accf868d4b538b82ba9f3b5aebb0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640780"
---
# <a name="atom-device-information-settings"></a><span data-ttu-id="d59a0-102">ATOM デバイス情報の設定</span><span class="sxs-lookup"><span data-stu-id="d59a0-102">ATOM Device Information Settings</span></span>
  <span data-ttu-id="d59a0-103">ATOM 表示拡張機能のデバイス情報設定では、ATOM フィードの名前および使用する文字エンコードの送信がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="d59a0-103">The device information settings for the Atom rendering extension support submittal of the name of an Atom feed and character encoding to use.</span></span>  
  
 <span data-ttu-id="d59a0-104">次の表は、データ サービス ドキュメントに表示するためのデバイス情報設定を示しています。</span><span class="sxs-lookup"><span data-stu-id="d59a0-104">The following table lists the device information settings for rendering to a data service document.</span></span>  
  
|<span data-ttu-id="d59a0-105">設定</span><span class="sxs-lookup"><span data-stu-id="d59a0-105">Setting</span></span>|<span data-ttu-id="d59a0-106">値</span><span class="sxs-lookup"><span data-stu-id="d59a0-106">Value</span></span>|  
|-------------|-----------|  
|`DataFeed`|<span data-ttu-id="d59a0-107">指定した場合、この設定で指定されたフィード名に対応する ATOM フィードが表示されます。</span><span class="sxs-lookup"><span data-stu-id="d59a0-107">If specified, renders the Atom feed corresponding to the feed name provided in this setting.</span></span> <span data-ttu-id="d59a0-108">指定しない場合は、レポートの ATOM サービス ドキュメントが表示されます。</span><span class="sxs-lookup"><span data-stu-id="d59a0-108">If not, renders the Atom service document for the report.</span></span> <span data-ttu-id="d59a0-109">データ フィード固有の自動生成された識別子です。</span><span class="sxs-lookup"><span data-stu-id="d59a0-109">The unique auto-generated identifier of the data feed.</span></span> <span data-ttu-id="d59a0-110">これは内部で使用される値であり、変更はしないでください。</span><span class="sxs-lookup"><span data-stu-id="d59a0-110">This  value is used internally and you should not change it.</span></span>|  
|<span data-ttu-id="d59a0-111">**エンコード**</span><span class="sxs-lookup"><span data-stu-id="d59a0-111">**Encoding**</span></span>|<span data-ttu-id="d59a0-112">.NET Framework でサポートされている文字エンコードの Internet Assigned Numbers Authority (IANA) 名。</span><span class="sxs-lookup"><span data-stu-id="d59a0-112">The Internet Assigned Numbers Authority (IANA) name of a character encoding that is supported by the .NET Framework.</span></span> <span data-ttu-id="d59a0-113">既定値は `UTF-8` です。</span><span class="sxs-lookup"><span data-stu-id="d59a0-113">The default value is `UTF-8`.</span></span> <span data-ttu-id="d59a0-114">他の値には、ASCII、UTF-7、UTF-16 などがあります。</span><span class="sxs-lookup"><span data-stu-id="d59a0-114">Examples of other values include ASCII, UTF-7, and UTF-16.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d59a0-115">参照</span><span class="sxs-lookup"><span data-stu-id="d59a0-115">See Also</span></span>  
 <xref:ReportExecution2005.ReportExecutionService.Render%2A>   
 <span data-ttu-id="d59a0-116">[表示拡張機能にデバイス情報設定を渡す](report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md) </span><span class="sxs-lookup"><span data-stu-id="d59a0-116">[Passing Device Information Settings to Rendering Extensions](report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md) </span></span>  
 <span data-ttu-id="d59a0-117">[RSReportServer.Configで表示拡張機能パラメーターをカスタマイズする](customize-rendering-extension-parameters-in-rsreportserver-config.md) </span><span class="sxs-lookup"><span data-stu-id="d59a0-117">[Customize Rendering Extension Parameters in RSReportServer.Config](customize-rendering-extension-parameters-in-rsreportserver-config.md) </span></span>  
 [<span data-ttu-id="d59a0-118">テクニカル リファレンス (SSRS)</span><span class="sxs-lookup"><span data-stu-id="d59a0-118">Technical Reference &#40;SSRS&#41;</span></span>](../../2014/reporting-services/technical-reference-ssrs.md)  
  
  
