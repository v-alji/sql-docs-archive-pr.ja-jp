---
title: セキュリティ拡張機能の実装 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- security [Reporting Services], extensions
- forms-based authentication [Reporting Services]
- custom authentication [Reporting Services]
- extensions [Reporting Services], custom security
ms.assetid: d2327e7c-0d48-49e3-bcd9-3bba4e67a68b
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: e5cf1fa6ce0e0a02a52e6a27f693c152d1f97152
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641474"
---
# <a name="implementing-a-security-extension"></a><span data-ttu-id="a73d9-102">セキュリティ拡張機能の実装</span><span class="sxs-lookup"><span data-stu-id="a73d9-102">Implementing a Security Extension</span></span>
  [!INCLUDE[msCoName](../../../includes/msconame-md.md)] <span data-ttu-id="a73d9-103">Windows 認証は、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] でレポートをセキュリティで保護する主要なシステムです。</span><span class="sxs-lookup"><span data-stu-id="a73d9-103">Windows Authentication is the primary system for securing reports in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].</span></span> <span data-ttu-id="a73d9-104">ただし、企業のカスタム セキュリティに対処するために、[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] のセキュリティ システムを拡張する必要が生じることもあります。</span><span class="sxs-lookup"><span data-stu-id="a73d9-104">In certain cases, however, you may need to extend the [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] security system to accommodate custom security in your enterprise.</span></span> <span data-ttu-id="a73d9-105">このような場合には、[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] API に備えられた開発プラットフォームを使用します。</span><span class="sxs-lookup"><span data-stu-id="a73d9-105">You can do this using the development platform provided by the [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] API.</span></span> <span data-ttu-id="a73d9-106">ここでは、[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] のセキュリティ拡張機能の概要について説明します。</span><span class="sxs-lookup"><span data-stu-id="a73d9-106">This section will present an overview of security extensions in [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="a73d9-107">[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] セキュリティ拡張機能の実装、配置、および削除の詳細については、「[SQL Server Reporting Services Product Samples](https://go.microsoft.com/fwlink/?LinkId=177889)」 (SQL Server Reporting Services 製品サンプル) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a73d9-107">For complete details about implementing, deploying, and removing a [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] security extension, please see [SQL Server Reporting Services Product Samples](https://go.microsoft.com/fwlink/?LinkId=177889).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a73d9-108">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="a73d9-108">In This Section</span></span>  
 [<span data-ttu-id="a73d9-109">セキュリティ拡張機能の概要</span><span class="sxs-lookup"><span data-stu-id="a73d9-109">Security Extensions Overview</span></span>](security-extensions-overview.md)  
 <span data-ttu-id="a73d9-110">Reporting Services セキュリティ拡張機能の概要です。</span><span class="sxs-lookup"><span data-stu-id="a73d9-110">Provides an overview of Reporting Services Security Extensions.</span></span>  
  
 [<span data-ttu-id="a73d9-111">Reporting Services での認証</span><span class="sxs-lookup"><span data-stu-id="a73d9-111">Authentication in Reporting Services</span></span>](authentication-in-reporting-services.md)  
 <span data-ttu-id="a73d9-112">[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] での認証について説明します。</span><span class="sxs-lookup"><span data-stu-id="a73d9-112">Discusses authentication in [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].</span></span>  
  
 [<span data-ttu-id="a73d9-113">Reporting Services での承認</span><span class="sxs-lookup"><span data-stu-id="a73d9-113">Authorization in Reporting Services</span></span>](authorization-in-reporting-services.md)  
 <span data-ttu-id="a73d9-114">[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] での承認について説明します。</span><span class="sxs-lookup"><span data-stu-id="a73d9-114">Covers authorization in [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a73d9-115">参照</span><span class="sxs-lookup"><span data-stu-id="a73d9-115">See Also</span></span>  
 <xref:Microsoft.ReportingServices.Interfaces>   
 <span data-ttu-id="a73d9-116">[Reporting Services の拡張機能](../reporting-services-extensions.md) </span><span class="sxs-lookup"><span data-stu-id="a73d9-116">[Reporting Services Extensions](../reporting-services-extensions.md) </span></span>  
 [<span data-ttu-id="a73d9-117">Reporting Services 拡張機能ライブラリ</span><span class="sxs-lookup"><span data-stu-id="a73d9-117">Reporting Services Extension Library</span></span>](../reporting-services-extension-library.md)  
  
  
