---
title: 配信拡張機能を実装する準備 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- interfaces [Reporting Services]
- delivery extensions [Reporting Services], implementing
ms.assetid: aee1608d-374f-4ad3-bc23-fe07fdaa52b7
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: bbf98286e6ed35542d8117b4b87b5ff3425def69
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646046"
---
# <a name="preparing-to-implement-a-delivery-extension"></a><span data-ttu-id="942d4-102">配信拡張機能を実装する準備</span><span class="sxs-lookup"><span data-stu-id="942d4-102">Preparing to Implement a Delivery Extension</span></span>
  <span data-ttu-id="942d4-103">[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 配信拡張機能を実装する前に、実装するインターフェイスを定義しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="942d4-103">Before you implement your [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] delivery extension, you should define the interfaces to implement.</span></span> <span data-ttu-id="942d4-104">最初に配信拡張機能の使用方法、配信拡張機能に必要な設定、およびレポート通知を配信するために実装が必要な特定の機能を決定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="942d4-104">You first need to decide how your delivery extension will be used, what settings your delivery extension will require, and the specific functionality you will need to implement in order to deliver report notifications.</span></span>  
  
 <span data-ttu-id="942d4-105">各 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 配信拡張機能は、次の機能を提供する必要があります。</span><span class="sxs-lookup"><span data-stu-id="942d4-105">Each [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] delivery extension must provide the following functionality:</span></span>  
  
-   <span data-ttu-id="942d4-106"><xref:Microsoft.ReportingServices.Interfaces.IExtension> インターフェイスの実装。拡張機能とローカライズされた拡張機能名を表します。</span><span class="sxs-lookup"><span data-stu-id="942d4-106">An <xref:Microsoft.ReportingServices.Interfaces.IExtension> interface implementation that represents the extension and a localized extension name.</span></span>  
  
-   <span data-ttu-id="942d4-107"><xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension> の実装。レポート通知をエンド ユーザーに配信するために使用できる配信拡張機能を作成します。</span><span class="sxs-lookup"><span data-stu-id="942d4-107">An <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension> implementation that creates a delivery extension that can be used to deliver report notifications to end users.</span></span>  
  
-   <span data-ttu-id="942d4-108">サブスクリプション用の特定のユーザー データを処理する機能。</span><span class="sxs-lookup"><span data-stu-id="942d4-108">The ability to process specific user data for a subscription.</span></span>  
  
 <span data-ttu-id="942d4-109">各配信拡張機能は、次の機能を含むように強化することができます。</span><span class="sxs-lookup"><span data-stu-id="942d4-109">Each delivery extension can be enhanced to include the following functionality:</span></span>  
  
-   <span data-ttu-id="942d4-110">[!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] ユーザー コントロールの実装。エンド ユーザーがレポート マネージャーを使用して、配信拡張機能を使用するレポート サブスクリプションを作成できます。</span><span class="sxs-lookup"><span data-stu-id="942d4-110">An [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] user control implementation that enables end users to use Report Manager to create report subscriptions that use the delivery extension.</span></span>  
  
 <span data-ttu-id="942d4-111">次の表では、配信拡張機能で使用できるインターフェイスとクラスについて説明します。</span><span class="sxs-lookup"><span data-stu-id="942d4-111">The following table describes the available interfaces and classes for delivery extensions.</span></span>  
  
|<span data-ttu-id="942d4-112">インターフェイスまたはクラス</span><span class="sxs-lookup"><span data-stu-id="942d4-112">Interface or class</span></span>|<span data-ttu-id="942d4-113">説明</span><span class="sxs-lookup"><span data-stu-id="942d4-113">Description</span></span>|  
|------------------------|-----------------|  
|<span data-ttu-id="942d4-114"><xref:Microsoft.ReportingServices.Interfaces.IExtension> インターフェイス</span><span class="sxs-lookup"><span data-stu-id="942d4-114"><xref:Microsoft.ReportingServices.Interfaces.IExtension> Interface</span></span>|<span data-ttu-id="942d4-115">[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] の拡張機能を表します。</span><span class="sxs-lookup"><span data-stu-id="942d4-115">Represents an extension in [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].</span></span>|  
|<span data-ttu-id="942d4-116"><xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension> インターフェイス</span><span class="sxs-lookup"><span data-stu-id="942d4-116"><xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension> Interface</span></span>|<span data-ttu-id="942d4-117">[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] の配信拡張機能を表します。</span><span class="sxs-lookup"><span data-stu-id="942d4-117">Represents a delivery extension in [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].</span></span>|  
|<span data-ttu-id="942d4-118"><xref:Microsoft.ReportingServices.Interfaces.IDeliveryReportServerInformation> インターフェイス</span><span class="sxs-lookup"><span data-stu-id="942d4-118"><xref:Microsoft.ReportingServices.Interfaces.IDeliveryReportServerInformation> Interface</span></span>|<span data-ttu-id="942d4-119">配信拡張機能に必要なレポート サーバーに関する情報を含みます (使用可能な表示拡張機能の一覧など)。</span><span class="sxs-lookup"><span data-stu-id="942d4-119">Contains information about the report server that is required by delivery extensions (for example, a list of the available rendering extensions).</span></span>|  
|<span data-ttu-id="942d4-120"><xref:Microsoft.ReportingServices.Interfaces.Setting> クラス</span><span class="sxs-lookup"><span data-stu-id="942d4-120"><xref:Microsoft.ReportingServices.Interfaces.Setting> Class</span></span>|<span data-ttu-id="942d4-121">拡張機能の設定を表します。</span><span class="sxs-lookup"><span data-stu-id="942d4-121">Represents a setting for an extension.</span></span>|  
|<span data-ttu-id="942d4-122"><xref:Microsoft.ReportingServices.Interfaces.Notification> クラス</span><span class="sxs-lookup"><span data-stu-id="942d4-122"><xref:Microsoft.ReportingServices.Interfaces.Notification> Class</span></span>|<span data-ttu-id="942d4-123">配信拡張機能がレポートの配信に使用するサブスクリプション情報を含みます。</span><span class="sxs-lookup"><span data-stu-id="942d4-123">Contains subscription information that delivery extensions use to deliver reports.</span></span>|  
|<span data-ttu-id="942d4-124"><xref:Microsoft.ReportingServices.Interfaces.Report> クラス</span><span class="sxs-lookup"><span data-stu-id="942d4-124"><xref:Microsoft.ReportingServices.Interfaces.Report> Class</span></span>|<span data-ttu-id="942d4-125">配信拡張機能によるユーザーへのレポート配信を可能にする、レポート固有の情報とメソッドを表します。</span><span class="sxs-lookup"><span data-stu-id="942d4-125">Represents report-specific information and methods that enable delivery extensions to deliver reports to users.</span></span>|  
|<span data-ttu-id="942d4-126"><xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> クラス</span><span class="sxs-lookup"><span data-stu-id="942d4-126"><xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> Class</span></span>|<span data-ttu-id="942d4-127">表示拡張機能からの出力を表します。</span><span class="sxs-lookup"><span data-stu-id="942d4-127">Represents the output from a rendering extension.</span></span> <span data-ttu-id="942d4-128"><xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> オブジェクトには、表示拡張機能によって返されたストリームを処理するために、配信拡張機能に必要な関連付けられたファイルの名前と種類の情報を含みます。</span><span class="sxs-lookup"><span data-stu-id="942d4-128">A <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> object contains the associated file name and type information that is required by the delivery extension in order to process the stream returned by the rendering extension.</span></span>|  
|<span data-ttu-id="942d4-129"><xref:Microsoft.ReportingServices.Interfaces.ISubscriptionBaseUIUserControl> インターフェイス</span><span class="sxs-lookup"><span data-stu-id="942d4-129"><xref:Microsoft.ReportingServices.Interfaces.ISubscriptionBaseUIUserControl> Interface</span></span>|<span data-ttu-id="942d4-130">レポート マネージャーのユーザーから配信拡張機能固有のサブスクリプション情報を取得する方法を表すユーザー コントロール (電子メール アドレスやファイル共有ディレクトリへのパスなど)。</span><span class="sxs-lookup"><span data-stu-id="942d4-130">A user control that represents the means to retrieve delivery extension-specific subscription information from the user in Report Manager (for example, an e-mail address or the path to a file share).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="942d4-131">参照</span><span class="sxs-lookup"><span data-stu-id="942d4-131">See Also</span></span>  
 <span data-ttu-id="942d4-132">[Reporting Services の拡張機能](../reporting-services-extensions.md) </span><span class="sxs-lookup"><span data-stu-id="942d4-132">[Reporting Services Extensions](../reporting-services-extensions.md) </span></span>  
 <span data-ttu-id="942d4-133">[配信拡張機能の実装](implementing-a-delivery-extension.md) </span><span class="sxs-lookup"><span data-stu-id="942d4-133">[Implementing a Delivery Extension](implementing-a-delivery-extension.md) </span></span>  
 [<span data-ttu-id="942d4-134">Reporting Services 拡張機能ライブラリ</span><span class="sxs-lookup"><span data-stu-id="942d4-134">Reporting Services Extension Library</span></span>](../reporting-services-extension-library.md)  
  
  
