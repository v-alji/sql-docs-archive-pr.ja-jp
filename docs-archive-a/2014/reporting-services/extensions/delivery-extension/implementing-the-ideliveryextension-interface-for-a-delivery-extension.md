---
title: 配信拡張機能に対する IDeliveryExtension インターフェイスの実装 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- delivery extensions [Reporting Services], attributes
- delivery extensions [Reporting Services], class creation
- IDeliveryExtension interface
ms.assetid: ab0344db-510b-403f-8dbf-b9831553765d
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: a0f9ab0767a09016d4f4bc1158988965bfc13b27
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646050"
---
# <a name="implementing-the-ideliveryextension-interface-for-a-delivery-extension"></a><span data-ttu-id="375ae-102">配信拡張機能に対する IDeliveryExtension インターフェイスの実装</span><span class="sxs-lookup"><span data-stu-id="375ae-102">Implementing the IDeliveryExtension Interface for a Delivery Extension</span></span>
  <span data-ttu-id="375ae-103">配信拡張機能のクラスは、通知のコンテンツに基づいてレポート通知をユーザーに配信する場合に使用します。</span><span class="sxs-lookup"><span data-stu-id="375ae-103">Your delivery extension class is used to deliver report notifications to users based on the contents of the notifications.</span></span> <span data-ttu-id="375ae-104">配信拡張機能のクラスは、配信拡張機能に渡すユーザー設定を検証するためのインフラストラクチャも提供します。</span><span class="sxs-lookup"><span data-stu-id="375ae-104">The delivery extension class also provides infrastructure for validating user settings that are passed to the delivery extension.</span></span> <span data-ttu-id="375ae-105">また、配信拡張機能のクラスには、クライアントが拡張機能の名前に関する情報を取得する場合に使用できる特定のプロパティ、拡張機能がサポートする設定、および配信拡張機能で使用できる表示形式が含まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="375ae-105">In addition, your delivery extension class should contain specific properties that clients can use to gain information about the name of the extension, the settings that the extension supports, and the rendering formats that are available to the delivery extension.</span></span>  
  
 <span data-ttu-id="375ae-106">![IDeliveryExtension インターフェイスの処理](../../media/bk-ext-02.gif "IDeliveryExtension インターフェイスの処理")</span><span class="sxs-lookup"><span data-stu-id="375ae-106">![IDeliveryExtension interface process](../../media/bk-ext-02.gif "IDeliveryExtension interface process")</span></span>  
<span data-ttu-id="375ae-107">IDeliveryExtension インターフェイスを使用すると、ユーザー データを検証できることに加えて、クライアントが必要な配信設定を学習することもできます。</span><span class="sxs-lookup"><span data-stu-id="375ae-107">The IDeliveryExtension interface allows validation of user data as well as for clients to learn about the required delivery settings</span></span>  
  
 <span data-ttu-id="375ae-108">配信拡張機能のクラスを作成するには、<xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension> および <xref:Microsoft.ReportingServices.Interfaces.IExtension> を実装します。</span><span class="sxs-lookup"><span data-stu-id="375ae-108">To create a delivery extension class, implement <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension> and <xref:Microsoft.ReportingServices.Interfaces.IExtension>.</span></span> <span data-ttu-id="375ae-109">**IDeliveryExtension** インターフェイスでは、配信拡張機能による <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension.Deliver%2A> メソッドを使用したレポート通知の配信、および <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension.ValidateUserData%2A> メソッドを使用した受信済み拡張機能設定の検証が可能です。</span><span class="sxs-lookup"><span data-stu-id="375ae-109">The **IDeliveryExtension** interface enables your delivery extension to deliver report notifications using the <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension.Deliver%2A> method and to validate incoming extension settings using the <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension.ValidateUserData%2A> method.</span></span> <span data-ttu-id="375ae-110">**IExtension** インターフェイスでは、配信拡張機能によるローカライズされた拡張機能名の実装、および [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 構成ファイルに格納された拡張機能固有の構成情報の処理が可能です。</span><span class="sxs-lookup"><span data-stu-id="375ae-110">The **IExtension** interface enables your delivery extension to implement a localized extension name and to process extension-specific configuration information stored in the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] configuration file.</span></span> <span data-ttu-id="375ae-111">**IExtension** を実装すると、配信拡張機能に <xref:Microsoft.ReportingServices.Interfaces.Extension.LocalizedName%2A> プロパティが含まれます。</span><span class="sxs-lookup"><span data-stu-id="375ae-111">By implementing **IExtension**, your delivery extension contains the <xref:Microsoft.ReportingServices.Interfaces.Extension.LocalizedName%2A> property.</span></span> <span data-ttu-id="375ae-112">[!INCLUDE[ssRS](../../../includes/ssrs.md)] 配信拡張機能で **LocalizedName** プロパティをサポートすることを強くお勧めします。これにより、レポート マネージャーなどのユーザー インターフェイスで使い慣れた拡張機能名がユーザーに表示されます。</span><span class="sxs-lookup"><span data-stu-id="375ae-112">It is strongly recommended that [!INCLUDE[ssRS](../../../includes/ssrs.md)] delivery extensions support the **LocalizedName** property, so that users encounter a familiar name for the extension in a user interface, such as Report Manager.</span></span>  
  
 <span data-ttu-id="375ae-113">配信拡張機能では **IDeliveryExtension** インターフェイスの **ExtensionSettings** プロパティも実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="375ae-113">Your delivery extension must also implement the **ExtensionSettings** property of the **IDeliveryExtension** interface.</span></span> <span data-ttu-id="375ae-114">レポート サーバーは、<xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension.ExtensionSettings%2A> プロパティから返された値を使用して、配信拡張機能が必要とする設定を評価します。</span><span class="sxs-lookup"><span data-stu-id="375ae-114">The report server uses the value returned by the <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension.ExtensionSettings%2A> property to evaluate the settings that a delivery extension requires.</span></span> <span data-ttu-id="375ae-115">配信拡張機能と対話するクライアントは、レポート サーバー Web サービスの <xref:ReportService2010.ReportingService2010.GetExtensionSettings%2A> メソッドを使用して、配信拡張機能の設定一覧を返します。</span><span class="sxs-lookup"><span data-stu-id="375ae-115">Clients that interact with delivery extensions use the <xref:ReportService2010.ReportingService2010.GetExtensionSettings%2A> method of the Report Server Web service to return a list of settings for the delivery extension.</span></span>  
  
 <span data-ttu-id="375ae-116">配信拡張機能のクラスを使用すると、RSReportServer.config ファイルに格納されたカスタム構成データを取得および処理することもできます。</span><span class="sxs-lookup"><span data-stu-id="375ae-116">You can also use your delivery extension class to retrieve and process custom configuration data stored in the RSReportServer.config file.</span></span> <span data-ttu-id="375ae-117">カスタム構成データの処理の詳細については、<xref:Microsoft.ReportingServices.Interfaces.IExtension.SetConfiguration%2A> メソッドを参照してください。</span><span class="sxs-lookup"><span data-stu-id="375ae-117">For more information about processing custom configuration data, see the <xref:Microsoft.ReportingServices.Interfaces.IExtension.SetConfiguration%2A> method.</span></span>  
  
 <span data-ttu-id="375ae-118">**IDeliveryExtension** クラスの実装例については、「[SQL Server Reporting Services Product Samples](https://go.microsoft.com/fwlink/?LinkId=177889)」 (SQL Server Reporting Services 製品サンプル) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="375ae-118">For a sample **IDeliveryExtension** class implementation, see [SQL Server Reporting Services Product Samples](https://go.microsoft.com/fwlink/?LinkId=177889).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="375ae-119">参照</span><span class="sxs-lookup"><span data-stu-id="375ae-119">See Also</span></span>  
 <span data-ttu-id="375ae-120">[配信拡張機能の実装](../delivery-extension/implementing-a-delivery-extension.md) </span><span class="sxs-lookup"><span data-stu-id="375ae-120">[Implementing a Delivery Extension](../delivery-extension/implementing-a-delivery-extension.md) </span></span>  
 [<span data-ttu-id="375ae-121">Reporting Services 拡張機能ライブラリ</span><span class="sxs-lookup"><span data-stu-id="375ae-121">Reporting Services Extension Library</span></span>](../reporting-services-extension-library.md)  
  
  
