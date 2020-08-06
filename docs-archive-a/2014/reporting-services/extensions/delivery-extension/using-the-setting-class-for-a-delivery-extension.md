---
title: 配信拡張機能に対する Setting クラスの使用 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- delivery extensions [Reporting Services], settings
- Setting class
ms.assetid: 50746639-da7c-46a5-ac7b-e87dd6b91880
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 594cf28391ae4523e1a95ad79ee5b1280ff72218
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87712806"
---
# <a name="using-the-setting-class-for-a-delivery-extension"></a><span data-ttu-id="1832d-102">配信拡張機能に対する Setting クラスの使用</span><span class="sxs-lookup"><span data-stu-id="1832d-102">Using the Setting Class for a Delivery Extension</span></span>
  <span data-ttu-id="1832d-103"><xref:Microsoft.ReportingServices.Interfaces.Setting> クラスは <xref:Microsoft.ReportingServices.Interfaces> 名前空間にあり、配信拡張機能の拡張機能設定に関する情報を表します。</span><span class="sxs-lookup"><span data-stu-id="1832d-103">The <xref:Microsoft.ReportingServices.Interfaces.Setting> class is located in the <xref:Microsoft.ReportingServices.Interfaces> namespace and represents information about extension settings for a delivery extension.</span></span> <span data-ttu-id="1832d-104"><xref:Microsoft.ReportingServices.Interfaces.Setting> クラスは、配信拡張機能が正しく機能するために必要な設定に関する情報を格納するインフラストラクチャを提供します。</span><span class="sxs-lookup"><span data-stu-id="1832d-104">The <xref:Microsoft.ReportingServices.Interfaces.Setting> class provides infrastructure for storing information about the settings that are required in order for a delivery extension to function properly.</span></span> <span data-ttu-id="1832d-105">たとえば、レポート サーバーの電子メール配信では、ユーザーは受信者のアドレス、送信者のアドレス、電子メールの件名など、電子メール配信に固有の設定を入力する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1832d-105">For example, in Report Server E-Mail delivery, a user is required to supply settings specific to e-mail delivery, such as the recipient's address, the sender's address, the subject line of the e-mail, and more.</span></span> <span data-ttu-id="1832d-106">カスタム配信プロバイダーの場合にも、通知とレポートを配信する配信拡張機能のために、特定の設定を入力するようにユーザーに求めます。</span><span class="sxs-lookup"><span data-stu-id="1832d-106">Undoubtedly, your custom delivery providers will require the user to supply specific settings in order for the delivery extension to deliver notifications and reports.</span></span>  
  
 <span data-ttu-id="1832d-107"><xref:Microsoft.ReportingServices.Interfaces.Setting> クラスは、<xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension.ExtensionSettings%2A> インターフェイスの <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension> プロパティを実装する場合に使用します。</span><span class="sxs-lookup"><span data-stu-id="1832d-107">The <xref:Microsoft.ReportingServices.Interfaces.Setting> class is used when implementing the <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension.ExtensionSettings%2A> property of the <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension> interface.</span></span> <span data-ttu-id="1832d-108">サブスクリプションまたは通知が作成された場合にユーザーが指定した拡張機能設定データを処理するためにも、<xref:Microsoft.ReportingServices.Interfaces.Setting> クラスを使用します。</span><span class="sxs-lookup"><span data-stu-id="1832d-108">The <xref:Microsoft.ReportingServices.Interfaces.Setting> class is also used for processing the extension setting data that is supplied by a user when a subscription or notification is created.</span></span>  
  
 <span data-ttu-id="1832d-109"><xref:Microsoft.ReportingServices.Interfaces.Setting> クラスの使用例については、「[SQL Server Reporting Services Product Samples](https://go.microsoft.com/fwlink/?LinkId=177889)」 (SQL Server Reporting Services 製品サンプル) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1832d-109">For an example of how to use the <xref:Microsoft.ReportingServices.Interfaces.Setting> class, see [SQL Server Reporting Services Product Samples](https://go.microsoft.com/fwlink/?LinkId=177889).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1832d-110">参照</span><span class="sxs-lookup"><span data-stu-id="1832d-110">See Also</span></span>  
 <span data-ttu-id="1832d-111">[配信拡張機能の実装](implementing-a-delivery-extension.md) </span><span class="sxs-lookup"><span data-stu-id="1832d-111">[Implementing a Delivery Extension](implementing-a-delivery-extension.md) </span></span>  
 [<span data-ttu-id="1832d-112">Reporting Services 拡張機能ライブラリ</span><span class="sxs-lookup"><span data-stu-id="1832d-112">Reporting Services Extension Library</span></span>](../reporting-services-extension-library.md)  
  
  
