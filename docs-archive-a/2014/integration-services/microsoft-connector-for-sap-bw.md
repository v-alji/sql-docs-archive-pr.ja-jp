---
title: SAP BW 用 Microsoft コネクタ 1.1 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 5281f080-53d5-4679-aa26-f4cd4ac7a2df
author: chugugrace
ms.author: chugu
ms.openlocfilehash: ec5cfe83b201976be0512c54b77bc79f8aa824b3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87736541"
---
# <a name="microsoft-connector-11-for-sap-bw"></a><span data-ttu-id="d09f9-102">Microsoft Connector 1.1 for SAP BW</span><span class="sxs-lookup"><span data-stu-id="d09f9-102">Microsoft Connector 1.1 for SAP BW</span></span>
  <span data-ttu-id="d09f9-103">[!INCLUDE[msCoName](../includes/msconame-md.md)]SAP BW のコネクタ1.1 は、SAP NETWEAVER BW version 7 システムからデータを抽出したり、データをデータに読み込んだりするための3つのコンポーネントのセットで構成されています。</span><span class="sxs-lookup"><span data-stu-id="d09f9-103">The [!INCLUDE[msCoName](../includes/msconame-md.md)] Connector 1.1 for SAP BW consists of a set of three components that let you extract data from, or load data into, an SAP Netweaver BW version 7 system.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="d09f9-104">Microsoft Connector 1.1 for SAP BW に関するドキュメントでは、SAP Netweaver BW 環境について理解していることを前提としています。</span><span class="sxs-lookup"><span data-stu-id="d09f9-104">The documentation for the Microsoft Connector 1.1 for SAP BW assumes familiarity with the SAP Netweaver BW environment.</span></span> <span data-ttu-id="d09f9-105">SAP Netweaver BW の詳細または SAP Netweaver BW オブジェクトやプロセスを構成する方法については、SAP のマニュアルを参照してください。</span><span class="sxs-lookup"><span data-stu-id="d09f9-105">For more information about SAP Netweaver BW, or for information about how to configure SAP Netweaver BW objects and processes, see your SAP documentation.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="d09f9-106">SAP Netweaver BW からデータを抽出するには、追加の SAP のライセンスが必要です。</span><span class="sxs-lookup"><span data-stu-id="d09f9-106">Extracting data from SAP Netweaver BW requires additional SAP licensing.</span></span> <span data-ttu-id="d09f9-107">これらの要件を確認するには、SAP にお問い合わせください。</span><span class="sxs-lookup"><span data-stu-id="d09f9-107">Check with SAP to verify these requirements.</span></span>  
  
## <a name="components"></a><span data-ttu-id="d09f9-108">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="d09f9-108">Components</span></span>  
 <span data-ttu-id="d09f9-109">[!INCLUDE[msCoName](../includes/msconame-md.md)]SAP BW のコネクタ1.1 には、次のコンポーネントがあります。</span><span class="sxs-lookup"><span data-stu-id="d09f9-109">The [!INCLUDE[msCoName](../includes/msconame-md.md)] Connector 1.1 for SAP BW has the following components:</span></span>  
  
-   <span data-ttu-id="d09f9-110">**SAP BW ソース**-SAP BW ソースは、SAP Netweaver BW version 7 システムからデータを抽出できるデータフローの変換元コンポーネントです。</span><span class="sxs-lookup"><span data-stu-id="d09f9-110">**SAP BW Source**-The SAP BW source is a data flow source component that lets you extract data from an SAP Netweaver BW version 7 system.</span></span>  
  
-   <span data-ttu-id="d09f9-111">**SAP BW destination**-SAP BW destination は、SAP Netweaver BW version 7 システムにデータを読み込むことができるデータフロー変換先コンポーネントです。</span><span class="sxs-lookup"><span data-stu-id="d09f9-111">**SAP BW Destination**-The SAP BW destination is a data flow destination component that lets you load data into an SAP Netweaver BW version 7 system.</span></span>  
  
-   <span data-ttu-id="d09f9-112">**SAP BW 接続マネージャー**-SAP BW 接続マネージャーは、SAP BW のソースまたは SAP BW の送信先を SAP Netweaver BW version 7 システムに接続します。</span><span class="sxs-lookup"><span data-stu-id="d09f9-112">**SAP BW Connection Manager**-The SAP BW connection manager connects either an SAP BW source or SAP BW destination to an SAP Netweaver BW version 7 system.</span></span>  
  
 <span data-ttu-id="d09f9-113">SAP BW 接続マネージャー、変換元、変換先の構成および使用方法の詳細については、ホワイト ペーパー「 [SAP BI 7.0 を使用した SQL Server Integration Services](https://go.microsoft.com/fwlink/?LinkId=301897)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d09f9-113">For a walkthrough that demonstrates how to configure and use the SAP BW connection manager, source, and destination, see the white paper, [Using SQL Server Integration Services with SAP BI 7.0](https://go.microsoft.com/fwlink/?LinkId=301897).</span></span> <span data-ttu-id="d09f9-114">このホワイト ペーパーには、SAP BW で必要なオブジェクトの構成方法についても説明されています。</span><span class="sxs-lookup"><span data-stu-id="d09f9-114">This white paper also shows how to configure the required objects in SAP BW.</span></span>  
  
## <a name="documentation"></a><span data-ttu-id="d09f9-115">ドキュメント</span><span class="sxs-lookup"><span data-stu-id="d09f9-115">Documentation</span></span>  
 <span data-ttu-id="d09f9-116">SAP BW のコネクタ1.1 のこのヘルプファイルに [!INCLUDE[msCoName](../includes/msconame-md.md)] は、次のトピックとセクションが含まれています。</span><span class="sxs-lookup"><span data-stu-id="d09f9-116">This Help file for the [!INCLUDE[msCoName](../includes/msconame-md.md)] Connector 1.1 for SAP BW contains the following topics and sections:</span></span>  
  
 [<span data-ttu-id="d09f9-117">Microsoft Connector 1.1 for SAP BW のインストール</span><span class="sxs-lookup"><span data-stu-id="d09f9-117">Installing the Microsoft Connector for 1.1 SAP BW</span></span>](installing-the-microsoft-connector-for-sap-bw.md)  
 <span data-ttu-id="d09f9-118">SAP BW のコネクタ1.1 のインストール要件について説明し [!INCLUDE[msCoName](../includes/msconame-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="d09f9-118">Describes the installation requirements for the [!INCLUDE[msCoName](../includes/msconame-md.md)] Connector 1.1 for SAP BW.</span></span>  
  
 [<span data-ttu-id="d09f9-119">Microsoft Connector 1.1 for SAP BW のコンポーネント</span><span class="sxs-lookup"><span data-stu-id="d09f9-119">Microsoft Connector 1.1 for SAP BW Components</span></span>](microsoft-connector-for-sap-bw-components.md)  
 <span data-ttu-id="d09f9-120">SAP BW のコネクタ1.1 の各コンポーネントについて説明し [!INCLUDE[msCoName](../includes/msconame-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="d09f9-120">Describes each component of the [!INCLUDE[msCoName](../includes/msconame-md.md)] Connector 1.1 for SAP BW.</span></span>  
  
 [<span data-ttu-id="d09f9-121">Microsoft Connector 1.1 for SAP BW の F1 ヘルプ</span><span class="sxs-lookup"><span data-stu-id="d09f9-121">Microsoft Connector 1.1 for SAP BW F1 Help</span></span>](microsoft-connector-for-sap-bw-f1-help.md)  
 <span data-ttu-id="d09f9-122">SAP BW のコネクタ1.1 の各コンポーネントのユーザーインターフェイスについて説明し [!INCLUDE[msCoName](../includes/msconame-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="d09f9-122">Describes the user interface of each component of the [!INCLUDE[msCoName](../includes/msconame-md.md)] Connector 1.1 for SAP BW.</span></span>  
  
  
