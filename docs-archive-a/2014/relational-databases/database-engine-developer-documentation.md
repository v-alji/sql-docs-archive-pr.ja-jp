---
title: Developer&#39;s ガイド (データベースエンジン) |Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- developer's guide [SQL Server Database Engine]
- Database Engine [SQL Server], development
ms.assetid: 7638f46c-9e66-48e6-9a9b-425e0b788311
author: rothja
ms.author: jroth
ms.openlocfilehash: e1f8c8022422def83229b72c6b6a061f12755328
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645126"
---
# <a name="developer39s-guide-database-engine"></a><span data-ttu-id="c39fa-102">Developer&#39;s ガイド (データベースエンジン)</span><span class="sxs-lookup"><span data-stu-id="c39fa-102">Developer&#39;s Guide (Database Engine)</span></span>
  [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] <span data-ttu-id="c39fa-103">には、データベース アプリケーションの開発、管理、および制御のための豊富なツールが用意されています。</span><span class="sxs-lookup"><span data-stu-id="c39fa-103">provides a rich set of tools for developing, administering, and controlling database applications.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c39fa-104">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="c39fa-104">In This Section</span></span>  
 [<span data-ttu-id="c39fa-105">CLR &#40;共通言語ランタイム&#41; 統合のプログラミング概念</span><span class="sxs-lookup"><span data-stu-id="c39fa-105">Common Language Runtime &#40;CLR&#41; Integration Programming Concepts</span></span>](clr-integration/common-language-runtime-clr-integration-programming-concepts.md)  
 <span data-ttu-id="c39fa-106">[!INCLUDE[msCoName](../includes/msconame-md.md)] での .NET Framework for [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Windows の CLR (共通言語ランタイム) コンポーネントの統合について説明します。</span><span class="sxs-lookup"><span data-stu-id="c39fa-106">Describes the integration of the common language runtime (CLR) component of the .NET Framework for [!INCLUDE[msCoName](../includes/msconame-md.md)] Windows in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="c39fa-107">つまり、[!INCLUDE[msCoName](../includes/msconame-md.md)] Visual Basic .NET や [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual C# などの .NET Framework 言語を使用して、ストアド プロシージャ、トリガー、ユーザー定義型、ユーザー定義関数、ユーザー定義集計、およびストリーミング テーブル値関数を記述できます。</span><span class="sxs-lookup"><span data-stu-id="c39fa-107">This means that you can write stored procedures, triggers, user-defined types, user-defined functions, user-defined aggregates, and streaming table-valued functions, using any .NET Framework language, including [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual Basic .NET and [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual C#.</span></span>  
  
 [<span data-ttu-id="c39fa-108">SQL Server Native Client プログラミング</span><span class="sxs-lookup"><span data-stu-id="c39fa-108">SQL Server Native Client Programming</span></span>](native-client/sql-server-native-client-programming.md)  
 <span data-ttu-id="c39fa-109">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Native Client を使用することで、MARS (複数のアクティブな結果セット)、UDT (ユーザー定義データ型)、クエリ通知、スナップショット分離、XML データ型のサポートなど、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] の新機能を利用して既存のアプリケーションを強化したり、新しいアプリケーションを作成したりする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="c39fa-109">Describes how [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Native Client can be used to create new applications or enhance existing applications to take advantage of new [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] features such as multiple active result sets (MARS), user-defined data types (UDT), query notifications, snapshot isolation, and XML data type support.</span></span>  
  
 [<span data-ttu-id="c39fa-110">SQLXML 4.0 のプログラミング概念</span><span class="sxs-lookup"><span data-stu-id="c39fa-110">SQLXML 4.0 Programming Concepts</span></span>](sqlxml/sqlxml-4-0-programming-concepts.md)  
 <span data-ttu-id="c39fa-111">SQLXML 3.0 と同じ機能に加えて、[!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)] で導入された xml データ型などの新機能に対応するための更新を提供する SQLXML の最新バージョンについて説明します。</span><span class="sxs-lookup"><span data-stu-id="c39fa-111">Describes the latest version of SQLXML, which delivers the same functionality as SQLXML 3.0 as well as additional updates to accommodate new features introduced in [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)], such as the xml data type.</span></span>  
  
 [<span data-ttu-id="c39fa-112">構成管理用の WMI プロバイダーの概念</span><span class="sxs-lookup"><span data-stu-id="c39fa-112">WMI Provider for Configuration Management Concepts</span></span>](wmi-provider-configuration/wmi-provider-for-configuration-management.md)  
 <span data-ttu-id="c39fa-113">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]Microsoft 管理コンソール (MMC) および Configuration Manager の Configuration Manager スナップインと共に使用される、公開されたレイヤーについて説明し [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="c39fa-113">Describes a published layer that is used with the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Configuration Manager snap-in for Microsoft Management Console (MMC) and the [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Configuration Manager.</span></span> <span data-ttu-id="c39fa-114">これにより、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 構成マネージャーから要求されたレジストリ操作を処理する API 呼び出しは、統一されたインターフェイスで操作できます。また、選択された [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] サービスに対して高度な制御および操作を行えます。</span><span class="sxs-lookup"><span data-stu-id="c39fa-114">It provides a unified way for interfacing with the API calls that manage the registry operations requested by [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Configuration Manager and provides enhanced control and manipulation over the selected [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] services.</span></span>  
  
 [<span data-ttu-id="c39fa-115">WMI Provider for Server Events の概念</span><span class="sxs-lookup"><span data-stu-id="c39fa-115">WMI Provider for Server Events Concepts</span></span>](wmi-provider-server-events/wmi-provider-for-server-events-concepts.md)  
 <span data-ttu-id="c39fa-116">WMI (Windows Management Instrumentation) を使用して [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のインスタンスのイベントを監視する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="c39fa-116">Describes how to use Windows Management Instrumentation (WMI) to monitor events in an instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
 [<span data-ttu-id="c39fa-117">SQL Server 管理オブジェクト &#40;SMO&#41; プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="c39fa-117">SQL Server Management Objects &#40;SMO&#41; Programming Guide</span></span>](server-management-objects-smo/sql-server-management-objects-smo-programming-guide.md)  
 <span data-ttu-id="c39fa-118">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] の管理に必要なあらゆる機能をプログラミングできるように設計されたオブジェクトの集まりである、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 管理オブジェクト (SMO) について説明します。</span><span class="sxs-lookup"><span data-stu-id="c39fa-118">Contains information about [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Management Objects (SMO), a collection of objects that are designed for programming all aspects of managing [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
 [<span data-ttu-id="c39fa-119">データベース エンジン拡張ストアド プロシージャ プログラミング</span><span class="sxs-lookup"><span data-stu-id="c39fa-119">Database Engine Extended Stored Procedure Programming</span></span>](database-engine-extended-stored-procedure-programming.md)  
 <span data-ttu-id="c39fa-120">拡張ストアド プロシージャを使用して、C などのプログラミング言語でユーザー独自の外部ルーチンを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="c39fa-120">Describes how to use extended stored procedures to create your own external routines in a programming language such as C.</span></span>  
  
 [<span data-ttu-id="c39fa-121">データ コレクターのプログラミング</span><span class="sxs-lookup"><span data-stu-id="c39fa-121">Data Collector Programming</span></span>](../database-engine/dev-guide/data-collector-programming.md)  
 <span data-ttu-id="c39fa-122">Data Collector オブジェクト モデルについて説明します。</span><span class="sxs-lookup"><span data-stu-id="c39fa-122">Describes the Data Collector object model.</span></span>  
  
 [<span data-ttu-id="c39fa-123">例外メッセージ ボックスのプログラミング</span><span class="sxs-lookup"><span data-stu-id="c39fa-123">Exception Message Box Programming</span></span>](../database-engine/dev-guide/exception-message-box-programming.md)  
 <span data-ttu-id="c39fa-124">アプリケーションに例外メッセージ ボックス プログラム インターフェイスを使用して、メッセージ エクスペリエンスを高い柔軟性で制御し、ユーザーが後で参照できるようにエラー メッセージを保存したり、メッセージのヘルプを表示したりできるようにする方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="c39fa-124">Describes how you can use the exception message box programmatic interface in your applications to provide more control over the messaging experience, to give your users the option to save error message content for later reference, and to get help with messages.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c39fa-125">参照</span><span class="sxs-lookup"><span data-stu-id="c39fa-125">See Also</span></span>  
 <span data-ttu-id="c39fa-126">[データマイニングのプログラミング](../analysis-services/dev-guide/data-mining-programming.md) </span><span class="sxs-lookup"><span data-stu-id="c39fa-126">[Data Mining Programming](../analysis-services/dev-guide/data-mining-programming.md) </span></span>  
 <span data-ttu-id="c39fa-127">[開発者ガイド &#40;Analysis Services&#41;](https://docs.microsoft.com/analysis-services/analysis-services-developer-documentation) </span><span class="sxs-lookup"><span data-stu-id="c39fa-127">[Developer's Guide &#40;Analysis Services&#41;](https://docs.microsoft.com/analysis-services/analysis-services-developer-documentation) </span></span>  
 <span data-ttu-id="c39fa-128">[開発者ガイド &#40;Integration Services&#41;](../integration-services/integration-services-developer-documentation.md) </span><span class="sxs-lookup"><span data-stu-id="c39fa-128">[Developer's Guide &#40;Integration Services&#41;](../integration-services/integration-services-developer-documentation.md) </span></span>  
 <span data-ttu-id="c39fa-129">[開発者ガイド &#40;レプリケーション&#41;](replication/concepts/replication-developer-documentation.md) </span><span class="sxs-lookup"><span data-stu-id="c39fa-129">[Developer's Guide &#40;Replication&#41;](replication/concepts/replication-developer-documentation.md) </span></span>  
 [<span data-ttu-id="c39fa-130">開発者ガイド &#40;Reporting Services&#41;</span><span class="sxs-lookup"><span data-stu-id="c39fa-130">Developer's Guide &#40;Reporting Services&#41;</span></span>](../reporting-services/reporting-services-developer-documentation.md)  
  
  
