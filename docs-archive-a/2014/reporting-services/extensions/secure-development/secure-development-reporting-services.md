---
title: セキュリティで保護された開発 (Reporting Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- development security [Reporting Services]
- security [Reporting Services], development
- security [Reporting Services], strategies
ms.assetid: 12161a6c-b93b-4312-9d27-0c922561eb9b
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 7ba284b9013c5da6b03cce06ec72deccb045cfad
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646029"
---
# <a name="secure-development-reporting-services"></a><span data-ttu-id="90b28-102">セキュリティで保護された開発 (Reporting Services)</span><span class="sxs-lookup"><span data-stu-id="90b28-102">Secure Development (Reporting Services)</span></span>
  <span data-ttu-id="90b28-103">[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] は、厳しく制約され、管理者が定義したセキュリティ コンテキストでコードを実行できる堅固なセキュリティ システムを備えています。</span><span class="sxs-lookup"><span data-stu-id="90b28-103">The [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] provides a robust security system that can run code in tightly constrained, administrator-defined security contexts.</span></span> [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] <span data-ttu-id="90b28-104">は、コード アクセス セキュリティまたは証拠ベース セキュリティとも呼ばれる [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] のセキュリティ システムを使用します。</span><span class="sxs-lookup"><span data-stu-id="90b28-104">uses the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] security system, known as code access security (or evidence-based security).</span></span> <span data-ttu-id="90b28-105">コード アクセス セキュリティの管理下では、リソースにアクセスする場合にユーザーが信頼されます。ただし、ユーザーが実行するコードが信頼されていない場合は、リソースへのアクセスが拒否されます。</span><span class="sxs-lookup"><span data-stu-id="90b28-105">Under code access security, a user may be trusted to access a resource, but if the code the user executes is not trusted, access to the resource will be denied.</span></span>  
  
 <span data-ttu-id="90b28-106">コードに基づいたセキュリティは、特定のユーザーに基づいたものとは異なり、カスタム アセンブリまたは [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 向けに開発するデータ、配信、表示、セキュリティの各拡張機能に対する権限の表現を許可します。</span><span class="sxs-lookup"><span data-stu-id="90b28-106">Security based on code, as opposed to specific users, permits security to be expressed for custom assemblies or data, delivery, rendering, and security extensions that you develop for [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].</span></span> <span data-ttu-id="90b28-107">拡張機能のコードは多数の [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] ユーザーによって実行される可能性があり、どのようなユーザーが実行するかは開発時にはわかりません。</span><span class="sxs-lookup"><span data-stu-id="90b28-107">Your extension code may be executed by any number of [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] users, all of whom are unknown at development time.</span></span> <span data-ttu-id="90b28-108">開発するカスタム アセンブリや拡張機能には、[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] の特定のセキュリティ ポリシーが必要です。</span><span class="sxs-lookup"><span data-stu-id="90b28-108">The custom assemblies or extensions that you develop require specific security policies in [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].</span></span> <span data-ttu-id="90b28-109">これらのセキュリティ ポリシーは、[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] の種類として表されます。</span><span class="sxs-lookup"><span data-stu-id="90b28-109">These security policies are represented as types in the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)].</span></span> <span data-ttu-id="90b28-110">コード アクセス セキュリティの詳細については、[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] ドキュメントの「コード アクセス セキュリティ」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="90b28-110">For a more information about code access security, see "Code Access Security" in the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] documentation.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="90b28-111">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="90b28-111">In This Section</span></span>  
 [<span data-ttu-id="90b28-112">Reporting Services のコード アクセス セキュリティ</span><span class="sxs-lookup"><span data-stu-id="90b28-112">Code Access Security in Reporting Services</span></span>](code-access-security-in-reporting-services.md)  
 <span data-ttu-id="90b28-113">[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] のカスタム アセンブリおよび拡張機能で使用するコード アクセス セキュリティとポリシー構成について説明します。</span><span class="sxs-lookup"><span data-stu-id="90b28-113">Introduces code access security and policy configuration for custom assemblies and extensions in [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].</span></span>  
  
 [<span data-ttu-id="90b28-114">セキュリティ ポリシーの概要</span><span class="sxs-lookup"><span data-stu-id="90b28-114">Understanding Security Policies</span></span>](understanding-security-policies.md)  
 <span data-ttu-id="90b28-115">[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] の各種アセンブリとコード アクセス セキュリティがコード権限に及ぼす影響について説明します。</span><span class="sxs-lookup"><span data-stu-id="90b28-115">Describes the various assembly types in [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] and how code access security affects code permissions.</span></span>  
  
 [<span data-ttu-id="90b28-116">Reporting Services セキュリティ ポリシー ファイルの使用</span><span class="sxs-lookup"><span data-stu-id="90b28-116">Using Reporting Services Security Policy Files</span></span>](using-reporting-services-security-policy-files.md)  
 <span data-ttu-id="90b28-117">各種 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] コンポーネントおよび対応するポリシー構成ファイルについて説明します。</span><span class="sxs-lookup"><span data-stu-id="90b28-117">Describes the different [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] components and the corresponding policy configuration files.</span></span>  
  
  
