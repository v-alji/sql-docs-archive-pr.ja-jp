---
title: ファイルとバージョン番号 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- SQL Server Management Objects, versions
- components [SMO]
- files [SMO], components
- SMO [SQL Server], versions
- versions [SMO]
ms.assetid: 510907b6-e7a9-41bd-b892-d6d99a5118e1
author: stevestein
ms.author: sstein
ms.openlocfilehash: f1a7286f15af28f97e488b8b40fd745a0d320108
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640873"
---
# <a name="files-and-version-numbers"></a><span data-ttu-id="3cddb-102">ファイルとバージョン番号</span><span class="sxs-lookup"><span data-stu-id="3cddb-102">Files and Version Numbers</span></span>
  <span data-ttu-id="3cddb-103">必要なすべての [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 管理オブジェクト (SMO) コンポーネントは、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] クライアントまたはサーバーのインスタンスの一部としてインストールされます。</span><span class="sxs-lookup"><span data-stu-id="3cddb-103">All required [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Management Objects (SMO) components are installed as part of an instance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] client or server.</span></span> <span data-ttu-id="3cddb-104">SMO は複数のマネージド アセンブリに実装されます。</span><span class="sxs-lookup"><span data-stu-id="3cddb-104">SMO is implemented in several managed assemblies.</span></span> <span data-ttu-id="3cddb-105">クライアント上またはサーバー上のいずれかで SMO アプリケーションを開発することができます。</span><span class="sxs-lookup"><span data-stu-id="3cddb-105">You can develop SMO applications on either a client or a server.</span></span>  
  
|<span data-ttu-id="3cddb-106">ディレクトリ</span><span class="sxs-lookup"><span data-stu-id="3cddb-106">Directory</span></span>|<span data-ttu-id="3cddb-107">ファイル</span><span class="sxs-lookup"><span data-stu-id="3cddb-107">File</span></span>|<span data-ttu-id="3cddb-108">説明</span><span class="sxs-lookup"><span data-stu-id="3cddb-108">Description</span></span>|  
|---------------|----------|-----------------|  
|[!INCLUDE[ssSampPathSDK](../../includes/sssamppathsdk-md.md)]|<span data-ttu-id="3cddb-109">Microsoft.SqlServer.ConnectionInfo.dll</span><span class="sxs-lookup"><span data-stu-id="3cddb-109">Microsoft.SqlServer.ConnectionInfo.dll</span></span>|<span data-ttu-id="3cddb-110">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスへの接続のサポートが含まれています。</span><span class="sxs-lookup"><span data-stu-id="3cddb-110">Contains support for connecting to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>|  
|[!INCLUDE[ssSampPathSDK](../../includes/sssamppathsdk-md.md)]|<span data-ttu-id="3cddb-111">Microsoft.SqlServer.ServiceBrokerEnum.dll</span><span class="sxs-lookup"><span data-stu-id="3cddb-111">Microsoft.SqlServer.ServiceBrokerEnum.dll</span></span>|<span data-ttu-id="3cddb-112">[!INCLUDE[msCoName](../../includes/msconame-md.md)] Service Broker のプログラミングのサポートが含まれています。</span><span class="sxs-lookup"><span data-stu-id="3cddb-112">Contains support for programming the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Service Broker.</span></span> <span data-ttu-id="3cddb-113">Service Broker にアクセスするプログラムにのみ必要です。</span><span class="sxs-lookup"><span data-stu-id="3cddb-113">This is required only in programs that access the Service Broker.</span></span>|  
|[!INCLUDE[ssSampPathSDK](../../includes/sssamppathsdk-md.md)]|<span data-ttu-id="3cddb-114">Microsoft.SqlServer.Smo.dll</span><span class="sxs-lookup"><span data-stu-id="3cddb-114">Microsoft.SqlServer.Smo.dll</span></span>|<span data-ttu-id="3cddb-115">SMO クラスの大部分が含まれます。</span><span class="sxs-lookup"><span data-stu-id="3cddb-115">Contains the most of the SMO classes.</span></span>|  
|[!INCLUDE[ssSampPathSDK](../../includes/sssamppathsdk-md.md)]|<span data-ttu-id="3cddb-116">Microsoft.SqlServer.SmoExtended.dll</span><span class="sxs-lookup"><span data-stu-id="3cddb-116">Microsoft.SqlServer.SmoExtended.dll</span></span><br /><br /> <span data-ttu-id="3cddb-117">Microsoft.SqlServer.Management.Sdk.Sfc.dll</span><span class="sxs-lookup"><span data-stu-id="3cddb-117">Microsoft.SqlServer.Management.Sdk.Sfc.dll</span></span><br /><br /> <span data-ttu-id="3cddb-118">Microsoft.SqlServer.SqlEnum.dll</span><span class="sxs-lookup"><span data-stu-id="3cddb-118">Microsoft.SqlServer.SqlEnum.dll</span></span>|<span data-ttu-id="3cddb-119">SMO クラスのサポートが含まれています。</span><span class="sxs-lookup"><span data-stu-id="3cddb-119">Contains support for the SMO classes.</span></span>|  
|[!INCLUDE[ssSampPathSDK](../../includes/sssamppathsdk-md.md)]|<span data-ttu-id="3cddb-120">Microsoft.SqlServer.WmiEnum.dll</span><span class="sxs-lookup"><span data-stu-id="3cddb-120">Microsoft.SqlServer.WmiEnum.dll</span></span>|<span data-ttu-id="3cddb-121">Windows Management Instrumentation (WMI) プロバイダー クラスが含まれています。</span><span class="sxs-lookup"><span data-stu-id="3cddb-121">Contains the Windows Management Instrumentation (WMI) Provider classes.</span></span> <span data-ttu-id="3cddb-122">WMI プロバイダー クラスを使用するプログラムにのみ必要です。</span><span class="sxs-lookup"><span data-stu-id="3cddb-122">This is required only for programs that use the WMI Provider classes.</span></span>|  
|[!INCLUDE[ssSampPathSDK](../../includes/sssamppathsdk-md.md)]|<span data-ttu-id="3cddb-123">Microsoft.SqlServer.RegSvrEnum.dll</span><span class="sxs-lookup"><span data-stu-id="3cddb-123">Microsoft.SqlServer.RegSvrEnum.dll</span></span>|<span data-ttu-id="3cddb-124">登録済みサーバー クラスが含まれています。</span><span class="sxs-lookup"><span data-stu-id="3cddb-124">Contains the Registered Server classes.</span></span> <span data-ttu-id="3cddb-125">登録済みサーバー クラスを使用するプログラムにのみ必要です。</span><span class="sxs-lookup"><span data-stu-id="3cddb-125">This is required only for programs that use the Registered Server classes.</span></span>|  
  
  
