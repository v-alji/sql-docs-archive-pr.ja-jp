---
title: rs.exe ユーティリティと Web サービスを使用したスクリプト | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- Web service [Reporting Services], scripts
- rs utility
- XML Web service [Reporting Services], scripts
- Report Server Web service, scripts
- scripts [Reporting Services], Web service
ms.assetid: 0ec5ac6e-b3cf-49cd-96f6-6b4b7dc29982
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 9d84bb8722fd31a08ff7788ad31c601b377c23d6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641980"
---
# <a name="script-with-the-rsexe-utility-and-the-web-service"></a><span data-ttu-id="54903-102">rs.exe ユーティリティと Web サービスを使用したスクリプト</span><span class="sxs-lookup"><span data-stu-id="54903-102">Script with the rs.exe Utility and the Web Service</span></span>
  <span data-ttu-id="54903-103">開発者およびレポート サーバー管理者は、 **rs** ユーティリティ (RS.exe) を使用してレポート サーバーを操作できます。</span><span class="sxs-lookup"><span data-stu-id="54903-103">Developers and report server administrators can perform operations on a report server through the use of the **rs** utility (RS.exe).</span></span> <span data-ttu-id="54903-104">このユーティリティでは、[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] で記述されたスクリプトを使用し、プログラムによってレポート サーバーを管理できます。</span><span class="sxs-lookup"><span data-stu-id="54903-104">Using this utility, you can programmatically administer a report server using scripts written with [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)].</span></span>  
  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="54903-105">スクリプトを使用すると、レポート サーバー Web サービスのあらゆる操作を実行できます。</span><span class="sxs-lookup"><span data-stu-id="54903-105">scripts can be used to run any of the Report Server Web service operations.</span></span> <span data-ttu-id="54903-106">スクリプトを使用すれば、サーバー上の複数のレポートにセキュリティをコピーしたり、アイテムを追加または削除したり、サーバー間でレポート サーバー アイテムをコピーすることができます。</span><span class="sxs-lookup"><span data-stu-id="54903-106">Scripting can be used to copy security to multiple reports on a server, to add and delete items, to copy report server items from one server to another and more.</span></span> <span data-ttu-id="54903-107">スクリプト環境の詳細については、「 [Reporting Services スクリプト ファイルを実行する](run-a-reporting-services-script-file.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="54903-107">For more information about the scripting environment, see [Run a Reporting Services Script File](run-a-reporting-services-script-file.md).</span></span> <span data-ttu-id="54903-108">スクリプト ファイルは特定の書式を使用しており、 [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] .NET で記述されます。</span><span class="sxs-lookup"><span data-stu-id="54903-108">Script files take a certain format and are written in [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] .NET.</span></span> <span data-ttu-id="54903-109">詳細については、「 [Reporting Services スクリプト ファイルを書式設定する](format-a-reporting-services-script-file.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="54903-109">For more information, see [Format a Reporting Services Script File](format-a-reporting-services-script-file.md).</span></span>  
  
 <span data-ttu-id="54903-110">スクリプトの例については、次を参照してください。</span><span class="sxs-lookup"><span data-stu-id="54903-110">For script samples, see the following:</span></span>  
  
 <span data-ttu-id="54903-111">[サンプル Reporting Services rs.exe レポートサーバー間でコンテンツを移行するためのスクリプト](sample-reporting-services-rs-exe-script-to-copy-content-between-report-servers.md)です。</span><span class="sxs-lookup"><span data-stu-id="54903-111">[Sample Reporting Services rs.exe Script to Migrate Content between Report Servers](sample-reporting-services-rs-exe-script-to-copy-content-between-report-servers.md).</span></span>  
  
 <span data-ttu-id="54903-112">[SQL Server Reporting Services 製品サンプル](https://go.microsoft.com/fwlink/?LinkId=177889)。</span><span class="sxs-lookup"><span data-stu-id="54903-112">[SQL Server Reporting Services Product Samples](https://go.microsoft.com/fwlink/?LinkId=177889).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54903-113">参照</span><span class="sxs-lookup"><span data-stu-id="54903-113">See Also</span></span>  
 <span data-ttu-id="54903-114">[配置タスクおよび管理タスクのスクリプト作成](script-deployment-and-administrative-tasks.md) </span><span class="sxs-lookup"><span data-stu-id="54903-114">[Script Deployment and Administrative Tasks](script-deployment-and-administrative-tasks.md) </span></span>  
 <span data-ttu-id="54903-115">[レポート サーバー Web サービス](../report-server-web-service/report-server-web-service.md) </span><span class="sxs-lookup"><span data-stu-id="54903-115">[Report Server Web Service](../report-server-web-service/report-server-web-service.md) </span></span>  
 <span data-ttu-id="54903-116">[テクニカル リファレンス (SSRS)](../technical-reference-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="54903-116">[Technical Reference &#40;SSRS&#41;](../technical-reference-ssrs.md) </span></span>  
 [<span data-ttu-id="54903-117">RS.exe ユーティリティ &#40;SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="54903-117">RS.exe Utility &#40;SSRS&#41;</span></span>](rs-exe-utility-ssrs.md)  
  
  
