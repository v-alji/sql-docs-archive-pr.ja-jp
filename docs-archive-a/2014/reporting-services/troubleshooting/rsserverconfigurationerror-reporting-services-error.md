---
title: rsServerConfigurationError - Reporting Services エラー | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- rsServerConfigurationError
ms.assetid: 0913afc2-34b4-4713-b570-cfd5718975ac
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 02f8a18c42715d1f118920614eb425820130dacb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737860"
---
# <a name="rsserverconfigurationerror---reporting-services-error"></a><span data-ttu-id="28f1f-102">rsServerConfigurationError - Reporting Services エラー</span><span class="sxs-lookup"><span data-stu-id="28f1f-102">rsServerConfigurationError - Reporting Services Error</span></span>
    
## <a name="details"></a><span data-ttu-id="28f1f-103">詳細</span><span class="sxs-lookup"><span data-stu-id="28f1f-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="28f1f-104">製品名</span><span class="sxs-lookup"><span data-stu-id="28f1f-104">Product Name</span></span>|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|<span data-ttu-id="28f1f-105">イベント ID</span><span class="sxs-lookup"><span data-stu-id="28f1f-105">Event ID</span></span>|<span data-ttu-id="28f1f-106">rsServerConfiguration</span><span class="sxs-lookup"><span data-stu-id="28f1f-106">rsServerConfiguration</span></span>|  
|<span data-ttu-id="28f1f-107">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="28f1f-107">Event Source</span></span>|<span data-ttu-id="28f1f-108">Microsoft.ReportingServices.Diagnostics.Utilities.ErrorStrings</span><span class="sxs-lookup"><span data-stu-id="28f1f-108">Microsoft.ReportingServices.Diagnostics.Utilities.ErrorStrings</span></span>|  
|<span data-ttu-id="28f1f-109">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="28f1f-109">Component</span></span>|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]|  
|<span data-ttu-id="28f1f-110">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="28f1f-110">Message Text</span></span>|<span data-ttu-id="28f1f-111">レポート サーバーで構成エラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="28f1f-111">The report server has encountered a configuration error.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="28f1f-112">説明</span><span class="sxs-lookup"><span data-stu-id="28f1f-112">Explanation</span></span>  
 <span data-ttu-id="28f1f-113">これは、レポート サーバーまたはレポート作成ツールの構成設定が無効な場合に発生する、一般的なエラーです。</span><span class="sxs-lookup"><span data-stu-id="28f1f-113">This is a general purpose error that occurs when either the report server or a report authoring tool has invalid configuration settings.</span></span> <span data-ttu-id="28f1f-114">通常、このエラーは、エラーの実際の原因を示す 2 番目のメッセージと共に表示されます。</span><span class="sxs-lookup"><span data-stu-id="28f1f-114">The error is usually accompanied by a second message that states the actual cause of the error.</span></span>  
  
 <span data-ttu-id="28f1f-115">考えられる原因を次に示します。</span><span class="sxs-lookup"><span data-stu-id="28f1f-115">The following list summarizes possible causes:</span></span>  
  
-   <span data-ttu-id="28f1f-116">RSReportServer.config ファイルまたは RSReportDesigner.config ファイルが見つからないか読み取ることができません。</span><span class="sxs-lookup"><span data-stu-id="28f1f-116">The RSReportServer.config or RSReportDesigner.config file cannot be found or read.</span></span>  
  
-   <span data-ttu-id="28f1f-117">一方の構成ファイル内の XML 要素が見つからないか無効です。</span><span class="sxs-lookup"><span data-stu-id="28f1f-117">XML elements in either configuration file are missing or invalid.</span></span>  
  
-   <span data-ttu-id="28f1f-118">1 つまたは複数の XML 要素の値が見つからないか無効です。</span><span class="sxs-lookup"><span data-stu-id="28f1f-118">Values for one or more XML elements are missing or invalid.</span></span>  
  
-   <span data-ttu-id="28f1f-119">レジストリ設定が無効です。</span><span class="sxs-lookup"><span data-stu-id="28f1f-119">Registry settings are invalid.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="28f1f-120">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="28f1f-120">User Action</span></span>  
 <span data-ttu-id="28f1f-121">構成ファイルを手動で編集した後にこのエラーが発生するようになった場合は、変更を破棄して以前の値を入力するか、バックアップがある場合は以前のバージョンを復元します。</span><span class="sxs-lookup"><span data-stu-id="28f1f-121">If this error began to occur after you manually edited a configuration file, remove your changes and enter the previous value, or restore a previous version if you have a backup.</span></span>  
  
 <span data-ttu-id="28f1f-122">エラーに関連するエラーメッセージの詳細情報を確認するには、 `rsServerConfiguration` レポートサーバーのトレースログファイルを確認します。このファイルは、\Microsoft SQL server の msrs12にあります。 \<instancename >\ レポート Services\logfiles</span><span class="sxs-lookup"><span data-stu-id="28f1f-122">To review additional error message information that accompanies the `rsServerConfiguration` error, review the report server trace log files, which are located at \Microsoft SQL Server\MSRS12.\<instancename >\Reporting Services\LogFiles.</span></span> <span data-ttu-id="28f1f-123">詳細については、「 [Reporting Services のログ ファイルとソース](../report-server/reporting-services-log-files-and-sources.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="28f1f-123">For more information, see [Reporting Services Log Files and Sources](../report-server/reporting-services-log-files-and-sources.md).</span></span>  
  
## <a name="internal-only"></a><span data-ttu-id="28f1f-124">内部使用のみ</span><span class="sxs-lookup"><span data-stu-id="28f1f-124">Internal-Only</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28f1f-125">参照</span><span class="sxs-lookup"><span data-stu-id="28f1f-125">See Also</span></span>  
 <span data-ttu-id="28f1f-126">[Reporting Services 構成ファイル](../report-server/reporting-services-configuration-files.md) </span><span class="sxs-lookup"><span data-stu-id="28f1f-126">[Reporting Services Configuration Files](../report-server/reporting-services-configuration-files.md) </span></span>  
 [<span data-ttu-id="28f1f-127">Reporting Services の構成ファイル &#40;RSreportserver.config&#41; の変更</span><span class="sxs-lookup"><span data-stu-id="28f1f-127">Modify a Reporting Services Configuration File &#40;RSreportserver.config&#41;</span></span>](../report-server/modify-a-reporting-services-configuration-file-rsreportserver-config.md)  
  
  
