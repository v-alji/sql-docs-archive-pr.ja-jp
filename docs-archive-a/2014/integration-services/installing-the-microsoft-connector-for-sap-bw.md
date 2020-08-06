---
title: Microsoft Connector for 1.1 SAP BW のインストール |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 3bfb9023-9597-4f59-9085-4b9057e7702e
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 0ef96f38054f04e71de72bda0bbb12f8f003ef20
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640147"
---
# <a name="installing-the-microsoft-connector-for-11-sap-bw"></a><span data-ttu-id="98963-102">Microsoft Connector 1.1 for SAP BW のインストール</span><span class="sxs-lookup"><span data-stu-id="98963-102">Installing the Microsoft Connector for 1.1 SAP BW</span></span>
  <span data-ttu-id="98963-103">[!INCLUDE[msCoName](../includes/msconame-md.md)]SAP BW とそのドキュメントのコネクタ1.1 をインストールするには、SQL Server Feature Pack Web ページから Windows インストーラーパッケージをダウンロードして実行します。</span><span class="sxs-lookup"><span data-stu-id="98963-103">To install the [!INCLUDE[msCoName](../includes/msconame-md.md)] Connector 1.1 for SAP BW and its documentation, download and run the Windows installer package from the SQL Server Feature Pack Web page.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="98963-104">Microsoft Connector 1.1 for SAP BW に関するドキュメントでは、SAP Netweaver BW 環境について理解していることを前提としています。</span><span class="sxs-lookup"><span data-stu-id="98963-104">The documentation for the Microsoft Connector 1.1 for SAP BW assumes familiarity with the SAP Netweaver BW environment.</span></span> <span data-ttu-id="98963-105">SAP Netweaver BW の詳細または SAP Netweaver BW オブジェクトやプロセスを構成する方法については、SAP のマニュアルを参照してください。</span><span class="sxs-lookup"><span data-stu-id="98963-105">For more information about SAP Netweaver BW, or for information about how to configure SAP Netweaver BW objects and processes, see your SAP documentation.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="98963-106">SAP Netweaver BW からデータを抽出するには、追加の SAP のライセンスが必要です。</span><span class="sxs-lookup"><span data-stu-id="98963-106">Extracting data from SAP Netweaver BW requires additional SAP licensing.</span></span> <span data-ttu-id="98963-107">これらの要件を確認するには、SAP にお問い合わせください。</span><span class="sxs-lookup"><span data-stu-id="98963-107">Check with SAP to verify these requirements.</span></span>  
  
## <a name="required-sap-files"></a><span data-ttu-id="98963-108">必要な SAP のファイル</span><span class="sxs-lookup"><span data-stu-id="98963-108">Required SAP Files</span></span>  
 <span data-ttu-id="98963-109">SAP BW にコネクタ1.1 を使用するには [!INCLUDE[msCoName](../includes/msconame-md.md)] 、Sap フロントエンドソフトウェア (SAP GUI) をローカルコンピューターにインストールする必要はありません。</span><span class="sxs-lookup"><span data-stu-id="98963-109">To use the [!INCLUDE[msCoName](../includes/msconame-md.md)] Connector 1.1 for SAP BW, you do not have to install the SAP Front End software (SAP GUI) on the local computer.</span></span>  
  
 <span data-ttu-id="98963-110">ただし、SAP の .NET コネクタ ファイルである librfc32.dll を、Windows フォルダー内の system サブフォルダーにコピーする必要があります</span><span class="sxs-lookup"><span data-stu-id="98963-110">However you must copy the SAP .NET connector file, librfc32.dll, into the system subfolder in the Windows folder.</span></span> <span data-ttu-id="98963-111">(通常は、このフォルダーの場所は、 **C:\Windows\system32**です)。</span><span class="sxs-lookup"><span data-stu-id="98963-111">(Typically, this folder location is **C:\Windows\system32**.)</span></span>  
  
## <a name="considerations-for-64-bit-computers"></a><span data-ttu-id="98963-112">64 ビット コンピューターに関する注意事項</span><span class="sxs-lookup"><span data-stu-id="98963-112">Considerations for 64-bit Computers</span></span>  
 <span data-ttu-id="98963-113">[!INCLUDE[msCoName](../includes/msconame-md.md)]コネクタ 1.1 for SAP BW は、Windows の64ビットバージョンを完全にサポートして [!INCLUDE[msCoName](../includes/msconame-md.md)] います。</span><span class="sxs-lookup"><span data-stu-id="98963-113">The [!INCLUDE[msCoName](../includes/msconame-md.md)] Connector 1.1 for SAP BW fully supports the 64-bit version of [!INCLUDE[msCoName](../includes/msconame-md.md)] Windows.</span></span> <span data-ttu-id="98963-114">64ビットコンピューターの場合、 [!INCLUDE[msCoName](../includes/msconame-md.md)] SAP BW のコネクタ1.1 には、次の追加要件があります。</span><span class="sxs-lookup"><span data-stu-id="98963-114">On a 64-bit computer, the [!INCLUDE[msCoName](../includes/msconame-md.md)] Connector 1.1 for SAP BW has the following additional requirements:</span></span>  
  
-   <span data-ttu-id="98963-115">任意の 64 ビット Windows オペレーティング システムで、パッケージを 64 ビット モードで実行するには、SAP GUI ファイルの 64 ビット バージョンである librfc32.dll を、Windows フォルダー内の **system32** フォルダーにコピーします</span><span class="sxs-lookup"><span data-stu-id="98963-115">To run packages in 64-bit mode on any 64-bit Windows operating system, copy the 64-bit version of the SAP GUI file, librfc32.dll, into the **system32** folder of the Windows folder.</span></span> <span data-ttu-id="98963-116">(通常は、このファイルの場所は、 **C:\Windows\system32**です)。</span><span class="sxs-lookup"><span data-stu-id="98963-116">(Typically, this file location is **C:\Windows\system32**.)</span></span>  
  
-   <span data-ttu-id="98963-117">任意の 64 ビット Windows オペレーティング システムで、パッケージを 32 ビット モードで実行するには、SAP GUI ファイルである librfc32.dll を、Windows フォルダー内の **SysWow64** フォルダーにコピーします</span><span class="sxs-lookup"><span data-stu-id="98963-117">To run packages in 32-bit mode on any 64-bit Windows operating system, copy the SAP GUI file, librfc32.dll, into the **SysWow64** folder of the Windows folder.</span></span> <span data-ttu-id="98963-118">(通常は、このフォルダーの場所は、 **C:\Windows\SysWow64**です)。</span><span class="sxs-lookup"><span data-stu-id="98963-118">(Typically, this folder location is **C:\Windows\SysWow64**.)</span></span>  
  
  
