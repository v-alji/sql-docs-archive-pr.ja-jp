---
title: '[サーバーのプロパティ] ([セキュリティ] ページ) - Reporting Services | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.swb.reportserver.serverproperties.security.f1
ms.assetid: f49aedc6-f145-4df1-8f69-d5d910f492c6
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: f709d42bf593b4933d9fc1fdc423c195967df382
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641974"
---
# <a name="server-properties-security-page---reporting-services"></a><span data-ttu-id="d0446-102">[サーバーのプロパティ]\([セキュリティ] ページ) - Reporting Services</span><span class="sxs-lookup"><span data-stu-id="d0446-102">Server Properties (Security Page) - Reporting Services</span></span>
  <span data-ttu-id="d0446-103">このページを使用すると、レポート サーバーを危険にさらす可能性のある機能を無効にできます。</span><span class="sxs-lookup"><span data-stu-id="d0446-103">Use this page to turn off features that can potentially compromise a report server.</span></span> <span data-ttu-id="d0446-104">これらの機能を無効にすることで一部の機能が制限されますが、特定の脅威を緩和することで、レポート サーバー全体のセキュリティを向上させることができます。</span><span class="sxs-lookup"><span data-stu-id="d0446-104">Turning off these features will limit some functionality, but can improve the overall security of the report server by mitigating specific threats.</span></span>  
  
 <span data-ttu-id="d0446-105">このページを開くには、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]を起動してレポート サーバー インスタンスに接続し、レポート サーバー名を右クリックして **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d0446-105">To open this page, start [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], connect to a report server instance, right-click the report server name, and select **Properties**.</span></span> <span data-ttu-id="d0446-106">**[セキュリティ]** をクリックすると、このページが開きます。</span><span class="sxs-lookup"><span data-stu-id="d0446-106">Click **Security** to open this page.</span></span>  
  
## <a name="options"></a><span data-ttu-id="d0446-107">Options</span><span class="sxs-lookup"><span data-stu-id="d0446-107">Options</span></span>  
 <span data-ttu-id="d0446-108">**[レポート データ ソースで Windows 統合セキュリティを有効にする]**</span><span class="sxs-lookup"><span data-stu-id="d0446-108">**Enable Windows integrated security for report data sources**</span></span>  
 <span data-ttu-id="d0446-109">レポートを要求したユーザーの Windows セキュリティ トークンを使用してレポート データ ソースに接続するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="d0446-109">Specify whether a connection to a report data source can be made using the Windows security token of the user who requested the report.</span></span>  
  
 <span data-ttu-id="d0446-110">この機能を無効にすると、レポート データ ソースのプロパティ ページにある Windows 統合セキュリティ機能は使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="d0446-110">If you turn off this feature, the Windows Integrated Security feature in the report data source property pages will be unavailable.</span></span> <span data-ttu-id="d0446-111">レポート データ ソースが Windows 統合セキュリティを使用するように構成されている場合、この機能を無効にすると、レポート サーバーによってすべてのデータ ソース接続プロパティが即時に更新され、資格情報が要求されるようになります。</span><span class="sxs-lookup"><span data-stu-id="d0446-111">If report data sources are configured for Windows integrated security and you subsequently turn off this feature, the report server will immediately update all data source connection properties to prompt for credentials.</span></span>  
  
 <span data-ttu-id="d0446-112">**[カスタム レポートを有効にする]**</span><span class="sxs-lookup"><span data-stu-id="d0446-112">**Enable Ad Hoc Reporting**</span></span>  
 <span data-ttu-id="d0446-113">ユーザーがレポート ビルダーのレポートからアドホック クエリを実行できるようにするかどうかを指定します。実行できるようにした場合は、ユーザーが対象データをクリックすると新しいレポートが自動的に生成されます。</span><span class="sxs-lookup"><span data-stu-id="d0446-113">Specify whether users can perform ad hoc queries from a Report Builder report, where new reports are automatically generated when a user clicks data of interest.</span></span>  
  
 <span data-ttu-id="d0446-114">このオプションの設定によって、レポート サーバー上の `EnableLoadReportDefinition` プロパティの設定が `True` になるか `False` になるかが決まります。</span><span class="sxs-lookup"><span data-stu-id="d0446-114">Setting this option determines whether the `EnableLoadReportDefinition` property on the report server is set to `True` or `False`.</span></span> <span data-ttu-id="d0446-115">このオプションをオフにするとプロパティが `False` に設定され、レポート サーバーはデータ探索中に作成されるクリックスルー レポートを生成しません。</span><span class="sxs-lookup"><span data-stu-id="d0446-115">If you clear this option, the property will be set to `False` and report server will not generate clickthrough reports that are created during data exploration.</span></span> <span data-ttu-id="d0446-116">`LoadReportDefinition` メソッドの呼び出しはすべてブロックされます。</span><span class="sxs-lookup"><span data-stu-id="d0446-116">All calls to the `LoadReportDefinition` method will be blocked.</span></span>  
  
 <span data-ttu-id="d0446-117">この機能を無効にすることで、悪意のあるユーザーによる `LoadReportDefinition` 要求でレポート サーバーが過負荷になるサービス拒否攻撃の脅威を軽減することができます。</span><span class="sxs-lookup"><span data-stu-id="d0446-117">Turning off this option mitigates a threat whereby a malicious user launches a denial of service attack by overloading the report server with `LoadReportDefinition` requests.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0446-118">参照</span><span class="sxs-lookup"><span data-stu-id="d0446-118">See Also</span></span>  
 <span data-ttu-id="d0446-119">[レポートサーバーのプロパティ &#40;Management Studio の設定&#41;](set-report-server-properties-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="d0446-119">[Set Report Server Properties &#40;Management Studio&#41;](set-report-server-properties-management-studio.md) </span></span>  
 <span data-ttu-id="d0446-120">[Management Studio でレポートサーバーに接続する](connect-to-a-report-server-in-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="d0446-120">[Connect to a Report Server in Management Studio](connect-to-a-report-server-in-management-studio.md) </span></span>  
 <span data-ttu-id="d0446-121">[レポートデータソースの資格情報と接続情報を指定してください](..[Management Studio の F1 ヘルプでレポートサーバーを](report-server-in-management-studio-f1-help.md)作成します (& o)。これには、レポートサーバーを使用します。</span><span class="sxs-lookup"><span data-stu-id="d0446-121">[Specify Credential and Connection Information for Report Data Sources](../report-data/specify-credential-and-connection-information-for-report-data-sources.md [Report Server in Management Studio F1 Help](report-server-in-management-studio-f1-help.md)</span></span>  
  
  
