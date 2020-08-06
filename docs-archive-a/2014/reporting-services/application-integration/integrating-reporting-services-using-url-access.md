---
title: URL アクセスを使用した Reporting Services の統合| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- URL access [Reporting Services], about URL access
- integrating reports [Reporting Services]
ms.assetid: f1014f7d-fafa-4aa8-8bd2-5bdba835d9b6
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: fedf4ce3011d9caae9d673acf354265537115057
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87719724"
---
# <a name="integrating-reporting-services-using-url-access"></a><span data-ttu-id="90a0f-102">URL アクセスを使用した Reporting Services の統合</span><span class="sxs-lookup"><span data-stu-id="90a0f-102">Integrating Reporting Services Using URL Access</span></span>
  <span data-ttu-id="90a0f-103">URL アクセスでは、レポート サーバー URL によりレポートにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="90a0f-103">With URL access, you access reports through a report server URL.</span></span> <span data-ttu-id="90a0f-104">URL 要求を使用すると、特定のレポート サーバー、およびレポート サーバー データベースのレポート、リソースなどのアイテムにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="90a0f-104">A URL request enables you to access a specific report server as well as the reports, resources, and other items in the report server database.</span></span> <span data-ttu-id="90a0f-105">また、ユーザーへのレポート表示とナビゲーション方法もカスタマイズできます。</span><span class="sxs-lookup"><span data-stu-id="90a0f-105">You can also customize the report viewing and navigation experience for your users.</span></span> <span data-ttu-id="90a0f-106">URL のクエリ文字列にはデバイス情報設定、およびレポートと特定の表示出力を対象としたレポート パラメーターが含まれます。</span><span class="sxs-lookup"><span data-stu-id="90a0f-106">The query string of the URL contains device information settings, as well as report parameters targeted at your report and the chosen rendering output.</span></span> <span data-ttu-id="90a0f-107">レポート サーバーで URL 要求を処理する方法は、URL を使用してアクセスするパラメーター、パラメーター プレフィックス、およびアイテムの種類によって異なります。</span><span class="sxs-lookup"><span data-stu-id="90a0f-107">The way the report server handles URL requests depends on the parameters, parameter prefixes, and type of item that you are accessing through the URL.</span></span>  
  
 <span data-ttu-id="90a0f-108">Windows 環境か Web 環境かにかかわらず、URL アクセスを使用して、開発するアプリケーションにレポートおよびその他のレポート サーバー アイテムへのハイパーリンクを埋め込むことができます。</span><span class="sxs-lookup"><span data-stu-id="90a0f-108">You can use URL access to embed hyperlinks to reports and other report server items in the applications that you develop, whether in a Windows or Web environment.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="90a0f-109">このセクションのトピックでは、統合に関する基本的な概念について説明します。</span><span class="sxs-lookup"><span data-stu-id="90a0f-109">The topics in the section provide you with some basic ideas for integration.</span></span> <span data-ttu-id="90a0f-110">この情報を使用して、独自の [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 統合シナリオの設計と開発を開始できます。</span><span class="sxs-lookup"><span data-stu-id="90a0f-110">You can use the information to begin to design and develop your own [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] integration scenarios.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="90a0f-111">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="90a0f-111">In This Section</span></span>  
 [<span data-ttu-id="90a0f-112">Web アプリケーションでの URL アクセスの使用</span><span class="sxs-lookup"><span data-stu-id="90a0f-112">Using URL Access in a Web Application</span></span>](integrating-reporting-services-using-url-access-web-application.md)  
 <span data-ttu-id="90a0f-113">URL アクセスを使用して [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] を Web 環境に統合する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="90a0f-113">Describes how to use URL access to integrate [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] into a Web environment.</span></span>  
  
 [<span data-ttu-id="90a0f-114">Windows アプリケーションでの URL アクセスの使用</span><span class="sxs-lookup"><span data-stu-id="90a0f-114">Using URL Access in a Windows Application</span></span>](integrating-reporting-services-using-url-access-windows-application.md)  
 <span data-ttu-id="90a0f-115">URL アクセスを使用して [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] を [!INCLUDE[msCoName](../../includes/msconame-md.md)] Win32 環境に統合する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="90a0f-115">Describes how to use URL access to integrate [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] into a [!INCLUDE[msCoName](../../includes/msconame-md.md)] Win32 environment.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90a0f-116">参照</span><span class="sxs-lookup"><span data-stu-id="90a0f-116">See Also</span></span>  
 <span data-ttu-id="90a0f-117">[アプリケーションへの Reporting Services の統合](../application-integration/integrating-reporting-services-into-applications.md) </span><span class="sxs-lookup"><span data-stu-id="90a0f-117">[Integrating Reporting Services into Applications](../application-integration/integrating-reporting-services-into-applications.md) </span></span>  
 [<span data-ttu-id="90a0f-118">URL アクセス (SSRS)</span><span class="sxs-lookup"><span data-stu-id="90a0f-118">URL Access &#40;SSRS&#41;</span></span>](../url-access-ssrs.md)  
  
  
