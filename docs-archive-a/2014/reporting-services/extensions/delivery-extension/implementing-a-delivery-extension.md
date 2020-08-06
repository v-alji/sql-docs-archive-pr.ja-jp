---
title: 配信拡張機能の実装 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- delivery [Reporting Services]
- custom delivery extensions [Reporting Services]
- extensions [Reporting Services], delivery
- delivery extensions [Reporting Services]
ms.assetid: 600cd229-efcd-480e-8c95-3c3c39ff4e7a
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: af1e804e029dae77fb7836577aa8d4a45ad20109
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646052"
---
# <a name="implementing-a-delivery-extension"></a><span data-ttu-id="4b041-102">配信拡張機能の実装</span><span class="sxs-lookup"><span data-stu-id="4b041-102">Implementing a Delivery Extension</span></span>
  <span data-ttu-id="4b041-103">ユーザーは [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] により、作成およびパブリッシュ後にさまざまな場所に配信できるレポートを作成およびパブリッシュできます。</span><span class="sxs-lookup"><span data-stu-id="4b041-103">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] enables users to create and publish reports that, once created and published, can be delivered to various locations.</span></span> <span data-ttu-id="4b041-104">さらに、[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] には配信拡張機能と配信 API も用意されています。開発者は別の配信拡張機能を作成し、[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] の配信機能をさらに拡張することもできます。</span><span class="sxs-lookup"><span data-stu-id="4b041-104">In addition, [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] includes several delivery extensions and a delivery API that enable developers to create additional delivery extensions to further extend the functionality of delivery in [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="4b041-105">配信拡張機能の実装例については、「[SQL Server Reporting Services Product Samples](https://go.microsoft.com/fwlink/?LinkId=177889)」 (SQL Server Reporting Services 製品サンプル) をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="4b041-105">For a sample implementation of a delivery extension, see [SQL Server Reporting Services Product Samples](https://go.microsoft.com/fwlink/?LinkId=177889).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="4b041-106">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="4b041-106">In This Section</span></span>  
 <span data-ttu-id="4b041-107">[配信拡張機能の概要] 配信拡張機能-overview.md)</span><span class="sxs-lookup"><span data-stu-id="4b041-107">[Delivery Extensions Overview]delivery-extensions-overview.md)</span></span>  
 <span data-ttu-id="4b041-108">[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] のカスタム配信拡張機能の記述方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="4b041-108">Introduces how to write a custom delivery extension for [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].</span></span>  
  
 [<span data-ttu-id="4b041-109">配信拡張機能を実装する準備</span><span class="sxs-lookup"><span data-stu-id="4b041-109">Preparing to Implement a Delivery Extension</span></span>](preparing-to-implement-a-delivery-extension.md)  
 <span data-ttu-id="4b041-110">[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 配信拡張機能を実装する場合に使用できるインターフェイスとクラスに加え、実装前に考慮する問題についても説明します。</span><span class="sxs-lookup"><span data-stu-id="4b041-110">Describes the interfaces and classes available when implementing an [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] delivery extension, as well as issues to consider before implementation.</span></span>  
  
 [<span data-ttu-id="4b041-111">配信拡張機能ライブラリの作成</span><span class="sxs-lookup"><span data-stu-id="4b041-111">Creating a Delivery Extension Library</span></span>](creating-a-delivery-extension-library.md)  
 <span data-ttu-id="4b041-112">[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 配信拡張機能の名前空間の割り当て、および配信拡張機能のライブラリ DLL へのコンパイルについて説明します。</span><span class="sxs-lookup"><span data-stu-id="4b041-112">Describes assigning a namespace for your [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] delivery extension and compiling your delivery extension into a library DLL.</span></span>  
  
 [<span data-ttu-id="4b041-113">配信拡張機能に対する IDeliveryExtension インターフェイスの実装</span><span class="sxs-lookup"><span data-stu-id="4b041-113">Implementing the IDeliveryExtension Interface for a Delivery Extension</span></span>](implementing-the-ideliveryextension-interface-for-a-delivery-extension.md)  
 <span data-ttu-id="4b041-114">配信拡張機能の属性、および独自の配信拡張機能クラスを実装する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="4b041-114">Describes the attributes of a delivery extension, and how to implement your own delivery extension class.</span></span>  
  
 [<span data-ttu-id="4b041-115">配信拡張機能での Notification クラスの使用</span><span class="sxs-lookup"><span data-stu-id="4b041-115">Using a Notification Class for a Delivery Extension</span></span>](using-a-notification-class-for-a-delivery-extension.md)  
 <span data-ttu-id="4b041-116">**Notification** クラスの属性、および配信拡張機能の実装での使用方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="4b041-116">Describes the attributes of a **Notification** class and how to use it in your delivery extension implementation.</span></span>  
  
 [<span data-ttu-id="4b041-117">配信拡張機能に対する Setting クラスの使用</span><span class="sxs-lookup"><span data-stu-id="4b041-117">Using the Setting Class for a Delivery Extension</span></span>](using-the-setting-class-for-a-delivery-extension.md)  
 <span data-ttu-id="4b041-118">**Setting** クラスの属性、および配信拡張機能の実装での使用方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="4b041-118">Describes the attributes of a **Setting** class and how to use it in your delivery extension implementation.</span></span>  
  
 [<span data-ttu-id="4b041-119">配信拡張機能での IDeliveryReportServerInformation インターフェイスの使用</span><span class="sxs-lookup"><span data-stu-id="4b041-119">Using the IDeliveryReportServerInformation Interface for a Delivery Extension</span></span>](using-the-ideliveryreportserverinformation-interface-for-a-delivery-extension.md)  
 <span data-ttu-id="4b041-120">**IDeliveryReportServerInformation** インターフェイスの属性、および配信拡張機能の実装での使用方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="4b041-120">Describes the attributes of a **IDeliveryReportServerInformation** interface and how to use it in your delivery extension implementation.</span></span>  
  
 [<span data-ttu-id="4b041-121">配信拡張機能での Report クラスの使用</span><span class="sxs-lookup"><span data-stu-id="4b041-121">Using the Report Class for a Delivery Extension</span></span>](using-the-report-class-for-a-delivery-extension.md)  
 <span data-ttu-id="4b041-122">**Report** クラスの属性、および配信拡張機能の実装での使用方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="4b041-122">Describes the attributes of a **Report** class and how to use it in your delivery extension implementation.</span></span>  
  
 [<span data-ttu-id="4b041-123">配信拡張機能での RenderedOutputFile クラスの使用</span><span class="sxs-lookup"><span data-stu-id="4b041-123">Using the RenderedOutputFile Class for a Delivery Extension</span></span>](using-the-renderedoutputfile-class-for-a-delivery-extension.md)  
 <span data-ttu-id="4b041-124">**RenderedOutputFile** クラスの属性、および配信拡張機能の実装での使用方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="4b041-124">Describes the attributes of a **RenderedOutputFile** class and how to use it in your delivery extension implementation.</span></span>  
  
 [<span data-ttu-id="4b041-125">配信拡張機能の ISubscriptionBaseUIUserControl インターフェイスの実装</span><span class="sxs-lookup"><span data-stu-id="4b041-125">Implementing the ISubscriptionBaseUIUserControl Interface for a Delivery Extension</span></span>](implementing-the-isubscriptionbaseuiusercontrol-interface.md)  
 <span data-ttu-id="4b041-126">配信拡張機能ユーザー コントロールの属性、およびサブスクリプションに独自のインターフェイスを実装する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="4b041-126">Describes the attributes of a delivery extension user control and how to implement your own user interface for a subscription.</span></span>  
  
 [<span data-ttu-id="4b041-127">配信拡張機能の配置</span><span class="sxs-lookup"><span data-stu-id="4b041-127">Deploying a Delivery Extension</span></span>](deploying-a-delivery-extension.md)  
 <span data-ttu-id="4b041-128">配信拡張機能の配置方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="4b041-128">Describes how to deploy your delivery extension.</span></span>  
  
 [<span data-ttu-id="4b041-129">配信拡張機能のコードのデバッグ</span><span class="sxs-lookup"><span data-stu-id="4b041-129">Debugging Delivery Extension Code</span></span>](debugging-delivery-extension-code.md)  
 <span data-ttu-id="4b041-130">配信拡張機能でのコードのデバッグ方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="4b041-130">Describes how to debug code in your delivery extension.</span></span>  
  
 [<span data-ttu-id="4b041-131">配信拡張機能の削除</span><span class="sxs-lookup"><span data-stu-id="4b041-131">Removing a Delivery Extension</span></span>](removing-a-delivery-extension.md)  
 <span data-ttu-id="4b041-132">レポート サーバーから配信拡張機能を削除する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="4b041-132">Describes how to remove a delivery extension from a report server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b041-133">参照</span><span class="sxs-lookup"><span data-stu-id="4b041-133">See Also</span></span>  
 <span data-ttu-id="4b041-134">[Reporting Services 拡張機能](../reporting-services-extensions.md) </span><span class="sxs-lookup"><span data-stu-id="4b041-134">[Reporting Services Extensions](../reporting-services-extensions.md) </span></span>  
 [<span data-ttu-id="4b041-135">Reporting Services 拡張機能ライブラリ</span><span class="sxs-lookup"><span data-stu-id="4b041-135">Reporting Services Extension Library</span></span>](../reporting-services-extension-library.md)  
  
  
