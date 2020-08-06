---
title: 配信拡張機能での Notification クラスの使用 | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- delivery extensions [Reporting Services], notifications
- notifications [Reporting Services]
- retry queues
- Nofication class
ms.assetid: 549c40c4-d33d-46c2-9d6a-7bbb671ac67a
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 8b274eb50405a02f4995b953611e50a234b11eab
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646043"
---
# <a name="using-a-notification-class-for-a-delivery-extension"></a><span data-ttu-id="0464f-102">配信拡張機能での Notification クラスの使用</span><span class="sxs-lookup"><span data-stu-id="0464f-102">Using a Notification Class for a Delivery Extension</span></span>
  <span data-ttu-id="0464f-103"><xref:Microsoft.ReportingServices.Interfaces.Notification> クラスは <xref:Microsoft.ReportingServices.Interfaces> 名前空間にあり、配信拡張機能がレポートの配信に使用するサブスクリプション情報を表します。</span><span class="sxs-lookup"><span data-stu-id="0464f-103">The <xref:Microsoft.ReportingServices.Interfaces.Notification> class is located in the <xref:Microsoft.ReportingServices.Interfaces> namespace and represents subscription information that delivery extensions use for delivering reports.</span></span> <span data-ttu-id="0464f-104"><xref:Microsoft.ReportingServices.Interfaces.Notification> クラスには、配信するレポートの表示、通知の状態の決定、およびユーザー データの設定に使用できる多数のプロパティが用意されています。</span><span class="sxs-lookup"><span data-stu-id="0464f-104">The <xref:Microsoft.ReportingServices.Interfaces.Notification> class provides a number of properties that can be used to render the reports for delivery, determine the status of the notification, and set user data.</span></span>

 <span data-ttu-id="0464f-105">![レポート通知プロセス](../../media/bk-ext-03.gif "レポートの通知プロセス")通知は、配信の中心的なオブジェクトです。</span><span class="sxs-lookup"><span data-stu-id="0464f-105">![Report notification process](../../media/bk-ext-03.gif "Report notification process") The notification is the central object of any delivery</span></span>

 <span data-ttu-id="0464f-106">カスタム配信拡張機能を使用するサブスクリプションに関連付けられたイベントが起動すると、<xref:Microsoft.ReportingServices.Interfaces.Report> オブジェクトを含む通知が作成されます。</span><span class="sxs-lookup"><span data-stu-id="0464f-106">When an event fires that is associated with a subscription that uses your custom delivery extension, a notification is created that contains a <xref:Microsoft.ReportingServices.Interfaces.Report> object.</span></span> <span data-ttu-id="0464f-107"><xref:Microsoft.ReportingServices.Interfaces.Report> オブジェクトは、特定のレポートをサポートされている表示形式で表示するための機能をカプセル化します。また、このオブジェクトには、サーバー上のレポートの URL やレポート名など、レポート関連のプロパティが含まれます。</span><span class="sxs-lookup"><span data-stu-id="0464f-107">The <xref:Microsoft.ReportingServices.Interfaces.Report> object encapsulates the functionality needed to render a given report to a supported rendering format and contains report-specific properties, such as the URL to the report on the server and the name of the report.</span></span> <span data-ttu-id="0464f-108"><xref:Microsoft.ReportingServices.Interfaces.Report> クラスの詳細については、「[配信拡張機能での Report クラスの使用](../delivery-extension/using-the-report-class-for-a-delivery-extension.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0464f-108">For more information about the <xref:Microsoft.ReportingServices.Interfaces.Report> class, see [Using the Report Class for a Delivery Extension](../delivery-extension/using-the-report-class-for-a-delivery-extension.md).</span></span>

 <span data-ttu-id="0464f-109"><xref:Microsoft.ReportingServices.Interfaces.Notification> オブジェクトは、表示拡張機能の <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension.Deliver%2A> メソッドに渡します。</span><span class="sxs-lookup"><span data-stu-id="0464f-109">You pass the <xref:Microsoft.ReportingServices.Interfaces.Notification> object to the <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension.Deliver%2A> method of your delivery extension.</span></span> <span data-ttu-id="0464f-110"><xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension.Deliver%2A> メソッドに、通知を処理してレポートを配信するためのコードが含まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="0464f-110">Your <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension.Deliver%2A> method should contain specific code to process the notification and to deliver the report.</span></span>

 <span data-ttu-id="0464f-111"><xref:Microsoft.ReportingServices.Interfaces.Notification> クラスの使用例については、「[SQL Server Reporting Services Product Samples](https://go.microsoft.com/fwlink/?LinkId=177889)」 (SQL Server Reporting Services 製品サンプル) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0464f-111">For an example of how to use the <xref:Microsoft.ReportingServices.Interfaces.Notification> class, see [SQL Server Reporting Services Product Samples](https://go.microsoft.com/fwlink/?LinkId=177889).</span></span>

## <a name="retry-functionality"></a><span data-ttu-id="0464f-112">再試行機能</span><span class="sxs-lookup"><span data-stu-id="0464f-112">Retry Functionality</span></span>
 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] <span data-ttu-id="0464f-113">では、すぐに配信できない通知に対する再試行キューを作成できます。</span><span class="sxs-lookup"><span data-stu-id="0464f-113">allows you to create a retry queue for notifications that cannot immediately be delivered.</span></span> <span data-ttu-id="0464f-114">レポート サーバーが配信拡張機能の <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension.Deliver%2A> メソッドを呼び出した後、配信拡張機能はレポート サーバーが後で配信を再試行するように要求できます。</span><span class="sxs-lookup"><span data-stu-id="0464f-114">After the report server invokes the <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension.Deliver%2A> method of a delivery extension, the delivery extension can request that the report server retry the delivery at a later point in time.</span></span> <span data-ttu-id="0464f-115">この場合、レポート サーバーは通知を内部キューに配置し、特定の時間が経過した後に配信を再試行します。</span><span class="sxs-lookup"><span data-stu-id="0464f-115">If this occurs, the report server places the notification in an internal queue and retries the delivery after a specific period of time has elapsed.</span></span> <span data-ttu-id="0464f-116">管理者は、**MaxNumberOfRetries** XML 要素と **PeriodBetweenRetries** XML 要素を使用して、RSReportServer.config ファイルの配信拡張機能セクションに、レポート サーバーが実行する再試行回数の最大数と再試行の間隔を構成できます。</span><span class="sxs-lookup"><span data-stu-id="0464f-116">Administrators can configure the maximum number of retry attempts that the report server performs and the period between retries in the delivery extension section of the RSReportServer.config file using the **MaxNumberOfRetries** XML element and the **PeriodBetweenRetries** XML element.</span></span> <span data-ttu-id="0464f-117">後の配信が成功するか、再試行の最大回数に達すると、通知が再試行キューから削除されます。</span><span class="sxs-lookup"><span data-stu-id="0464f-117">Notifications are removed from the retry queue if delivery later succeeds or if the maximum number of retry attempts is reached.</span></span> <span data-ttu-id="0464f-118">再試行の最大回数後に配信が失敗すると、通知が破棄されます。</span><span class="sxs-lookup"><span data-stu-id="0464f-118">If delivery fails after the maximum number of retries, the notification is discarded.</span></span>

## <a name="see-also"></a><span data-ttu-id="0464f-119">参照</span><span class="sxs-lookup"><span data-stu-id="0464f-119">See Also</span></span>
 <span data-ttu-id="0464f-120">[拡張ライブラリ Reporting Services](../reporting-services-extension-library.md) [配信拡張機能の実装](../delivery-extension/implementing-a-delivery-extension.md)</span><span class="sxs-lookup"><span data-stu-id="0464f-120">[Implementing a Delivery Extension](../delivery-extension/implementing-a-delivery-extension.md) [Reporting Services Extension Library](../reporting-services-extension-library.md)</span></span>


