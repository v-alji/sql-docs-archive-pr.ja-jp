---
title: CDC デザイナー コンソールの概要 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 45298179-4ac1-4723-8b3c-56f5926be40a
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 888b111790cf3979e9d08a78502d24880fa034b0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632031"
---
# <a name="the-cdc-designer-console-introduction"></a><span data-ttu-id="5f671-102">CDC デザイナー コンソールの概要</span><span class="sxs-lookup"><span data-stu-id="5f671-102">The CDC Designer Console Introduction</span></span>
  <span data-ttu-id="5f671-103">ここでは、Change Data Capture Designer for Oracle by Attunity のインストール手順について説明します。</span><span class="sxs-lookup"><span data-stu-id="5f671-103">The section describes the installation procedures for the Change Data Capture Designer for Oracle by Attunity.</span></span>  
  
## <a name="installation"></a><span data-ttu-id="5f671-104">インストール</span><span class="sxs-lookup"><span data-stu-id="5f671-104">Installation</span></span>  
 <span data-ttu-id="5f671-105">ここでは、Change Data Capture Designer for Oracle by Attunity のインストール手順について説明します。</span><span class="sxs-lookup"><span data-stu-id="5f671-105">The section describes the installation procedures for the Change Data Capture Designer for Oracle by Attunity.</span></span> <span data-ttu-id="5f671-106">CDC Designer コンソールをインストールするには、SQL Server のインストールメディアから手動で**AttunityOracleCdcDesigner.msi**を実行します。</span><span class="sxs-lookup"><span data-stu-id="5f671-106">To install the CDC Designer Console, manually run **AttunityOracleCdcDesigner.msi** from the SQL Server installation media.</span></span>  <span data-ttu-id="5f671-107">X86 および x64 用のインストールパッケージは、SQL Server インストールメディアの \*\*.\Tools\AttunityCDCOracle \\ \*\*にあります。</span><span class="sxs-lookup"><span data-stu-id="5f671-107">Installation packages for x86 and x64 are located in **.\Tools\AttunityCDCOracle\\** on the SQL Server installation media.</span></span>  
  
## <a name="supported-windows-environments"></a><span data-ttu-id="5f671-108">サポートされている Windows 環境</span><span class="sxs-lookup"><span data-stu-id="5f671-108">Supported Windows Environments</span></span>  
 <span data-ttu-id="5f671-109">CDC デザイナー コンソールは、次の Windows 環境で実行できます。</span><span class="sxs-lookup"><span data-stu-id="5f671-109">The CDC Designer Console can run in the following Windows environments:</span></span>  
  
-   <span data-ttu-id="5f671-110">Windows Vista Service Pack 2 (32 ビット (x86) および 64 ビット (x64))</span><span class="sxs-lookup"><span data-stu-id="5f671-110">Windows Vista 32-bit (x86) and 64-bit (x64) with Service Pack 2</span></span>  
  
-   <span data-ttu-id="5f671-111">Windows 7 32 ビット (x86) および 64 ビット (x64)</span><span class="sxs-lookup"><span data-stu-id="5f671-111">Windows 7 32-bit (x86) and 64-bit (x64)</span></span>  
  
-   <span data-ttu-id="5f671-112">Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="5f671-112">Windows Server 2008 R2</span></span>  
  
-   <span data-ttu-id="5f671-113">Windows Server 2008 Service Pack 2 (32 ビット (x86) および 64 ビット (x64))</span><span class="sxs-lookup"><span data-stu-id="5f671-113">Windows Server 2008 32-bit (x86) and 64-bit (x64) with Service Pack 2</span></span>  
  
## <a name="database-prerequisites"></a><span data-ttu-id="5f671-114">データベースの前提条件</span><span class="sxs-lookup"><span data-stu-id="5f671-114">Database Prerequisites</span></span>  
 <span data-ttu-id="5f671-115">Change Data Capture Designer for Oracle by Attunity を使用するには、Oracle データベースを使用します。</span><span class="sxs-lookup"><span data-stu-id="5f671-115">To work with the Change Data Capture Designer for Oracle by Attunity, you work with an Oracle database.</span></span> <span data-ttu-id="5f671-116">Change Data Capture Designer for Oracle by Attunity でサポートされるバージョンは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="5f671-116">The Change Data Capture Designer for Oracle by Attunity supports the following versions:</span></span>  
  
 <span data-ttu-id="5f671-117">**Oracle データベース**</span><span class="sxs-lookup"><span data-stu-id="5f671-117">**Oracle Database**</span></span>  
  
-   <span data-ttu-id="5f671-118">Oracle Database 10g Release 2: 10.2.0.1 ～ 10.2.0.5 (2010 年 4 月の時点のパッチセット)</span><span class="sxs-lookup"><span data-stu-id="5f671-118">Oracle Database 10g Release 2: 10.2.0.1-10.2.0.5 (patchset as of April 2010)</span></span>  
  
-   <span data-ttu-id="5f671-119">Oracle Database 11g Release 1: 11.1.0.6 ～ 11.1.0.7 (2008 年 9 月の時点のパッチセット)</span><span class="sxs-lookup"><span data-stu-id="5f671-119">Oracle Database 11g Release 1: 11.1.0.6-11.1.0.7 (patchset as of September 2008)</span></span>  
  
-   <span data-ttu-id="5f671-120">Oracle Database 11g Release 2: 11.2.0.1 ～ 11.2.0.3 (2011 年 9 月の時点のパッチセット)</span><span class="sxs-lookup"><span data-stu-id="5f671-120">Oracle Database 11g Release 2: 11.2.0.1-11.2.0.3 (patchset as of September 2011)</span></span>  
  
 <span data-ttu-id="5f671-121">**SQL Server データベース**</span><span class="sxs-lookup"><span data-stu-id="5f671-121">**SQL Server Database**</span></span>  
  
-   [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] <span data-ttu-id="5f671-122">のエディション</span><span class="sxs-lookup"><span data-stu-id="5f671-122">edition with support for SQL Server CDC</span></span>  
  
## <a name="software-prerequisites"></a><span data-ttu-id="5f671-123">ソフトウェアの必要なコンポーネント</span><span class="sxs-lookup"><span data-stu-id="5f671-123">Software Prerequisites</span></span>  
 <span data-ttu-id="5f671-124">次のソフトウェアが必要です。</span><span class="sxs-lookup"><span data-stu-id="5f671-124">The following software is required:</span></span>  
  
-   <span data-ttu-id="5f671-125">Oracle 10 .x クライアント</span><span class="sxs-lookup"><span data-stu-id="5f671-125">Oracle 10.x client</span></span>  
  
-   <span data-ttu-id="5f671-126">Oracle 11.x クライアント</span><span class="sxs-lookup"><span data-stu-id="5f671-126">Oracle 11.x client</span></span>  
  
 <span data-ttu-id="5f671-127">**注**: インストールされている Oracle CDC Designer コンソールのバージョンに応じて、このソフトウェアの32ビット版または64ビット版を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5f671-127">**Note**: You must use the 32-bit or 64-bit version of this software according to the version of the Oracle CDC Designer console installed.</span></span>  
  
 <span data-ttu-id="5f671-128">Oracle CDC デザイナー コンソールでは、Oracle ODBC プロバイダーを使用してソースの Oracle データベースと通信します。</span><span class="sxs-lookup"><span data-stu-id="5f671-128">The Oracle CDC Designer Console uses the Oracle ODBC provider to communicate with the source Oracle database.</span></span>  
  
## <a name="running-the-installation-program"></a><span data-ttu-id="5f671-129">インストール プログラムの実行</span><span class="sxs-lookup"><span data-stu-id="5f671-129">Running the Installation Program</span></span>  
 <span data-ttu-id="5f671-130">ここでは、CDC デザイナー コンソールをインストールする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="5f671-130">This section describes how to install the CDC Designer Console.</span></span>  
  
 <span data-ttu-id="5f671-131">**CDC デザイナー コンソールをインストールするには**</span><span class="sxs-lookup"><span data-stu-id="5f671-131">**To install the CDC Designer Console**</span></span>  
  
 <span data-ttu-id="5f671-132">CDC デザイナー コンソール インストール キットをダブルクリックし、インストール ウィザードの指示に従います。</span><span class="sxs-lookup"><span data-stu-id="5f671-132">Double-click the CDC Designer Console installation kit and follow the directions in the installation wizard.</span></span>  
  
## <a name="uninstalling-the-cdc-designer-console"></a><span data-ttu-id="5f671-133">CDC デザイナー コンソールのアンインストール</span><span class="sxs-lookup"><span data-stu-id="5f671-133">Uninstalling the CDC Designer Console</span></span>  
 <span data-ttu-id="5f671-134">CDC デザイナー コンソールをアンインストールするには、コントロール パネルの [プログラムと機能] を使用します。</span><span class="sxs-lookup"><span data-stu-id="5f671-134">You uninstall the CDC Designer Console using Control Panel, Programs and Features.</span></span>  
  
  
