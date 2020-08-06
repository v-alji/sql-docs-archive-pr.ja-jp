---
title: 互換性のないデータベースエンジンサーバーの照合順序 (アップグレードアドバイザー) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 80f499d6-2c90-49eb-a5b3-0bb5b7faaa3b
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: b6ce0555bdf5a878e56d87a8bd55b5ce6c4b2649
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644792"
---
# <a name="incompatible-database-engine-server-collation-upgrade-advisor"></a><span data-ttu-id="5aa36-102">互換性のないデータベース エンジン サーバーの照合順序 (アップグレード アドバイザー)</span><span class="sxs-lookup"><span data-stu-id="5aa36-102">Incompatible Database Engine Server Collation (Upgrade Advisor)</span></span>
  <span data-ttu-id="5aa36-103">アップグレードアドバイザーにより [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 、 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 互換性のないサーバー照合順序を使用するように構成されたのインスタンスが使用されていることが検出されました。</span><span class="sxs-lookup"><span data-stu-id="5aa36-103">Upgrade Advisor detected [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] is using an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] that is configured to use an incompatible server collation.</span></span>  
  
||  
|-|  
|<span data-ttu-id="5aa36-104">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]SharePoint モード。</span><span class="sxs-lookup"><span data-stu-id="5aa36-104">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint mode.</span></span>|  
  
## <a name="component"></a><span data-ttu-id="5aa36-105">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="5aa36-105">Component</span></span>  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
## <a name="description"></a><span data-ttu-id="5aa36-106">説明</span><span class="sxs-lookup"><span data-stu-id="5aa36-106">Description</span></span>  
 <span data-ttu-id="5aa36-107">アップグレードアドバイザーにより [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 、 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 互換性のないサーバー照合順序を使用するように構成されたのインスタンスが使用されていることが検出されました。</span><span class="sxs-lookup"><span data-stu-id="5aa36-107">Upgrade Advisor detected [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] is using an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] that is configured to use an incompatible server collation.</span></span>  
  
 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<span data-ttu-id="5aa36-108">Sharepoint [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] モードでは、sharepoint 共有サービスアーキテクチャを利用します。</span><span class="sxs-lookup"><span data-stu-id="5aa36-108">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint mode utilizes the SharePoint shared services architecture.</span></span> <span data-ttu-id="5aa36-109">SharePoint では、大文字と小文字の区別、サーバー照合順序、またはバイナリ サーバー照合順序用に構成された [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] はサポートされません。</span><span class="sxs-lookup"><span data-stu-id="5aa36-109">SharePoint does not support [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] configured for case sensitive or server collations or binary server collations.</span></span> <span data-ttu-id="5aa36-110">互換性のない照合順序には、既定で大文字と小文字を区別するかバイナリである照合順序と、既定では互換性があるものの、次の照合順序指定子のいずれかで構成されている基本照合順序が含まれます。</span><span class="sxs-lookup"><span data-stu-id="5aa36-110">Incompatible collations include collations that are by default case sensitive or binary and a base collation that by default is compatible but has been configured with any of the following collation designators:</span></span>  
  
-   <span data-ttu-id="5aa36-111">**Binary**</span><span class="sxs-lookup"><span data-stu-id="5aa36-111">**Binary**</span></span>  
  
-   <span data-ttu-id="5aa36-112">**大文字と小文字を区別する**</span><span class="sxs-lookup"><span data-stu-id="5aa36-112">**Case-sensitive**</span></span>  
  
-   <span data-ttu-id="5aa36-113">**バイナリ コード ポイント**</span><span class="sxs-lookup"><span data-stu-id="5aa36-113">**Binary-codepoint**</span></span>  
  
 <span data-ttu-id="5aa36-114">現在の [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] サーバー照合順序は互換性がないため、アップグレードがブロックされます。</span><span class="sxs-lookup"><span data-stu-id="5aa36-114">Because the current [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] server collation is incompatible, upgrade is blocked.</span></span>  
  
## <a name="corrective-action"></a><span data-ttu-id="5aa36-115">修正措置</span><span class="sxs-lookup"><span data-stu-id="5aa36-115">Corrective Action</span></span>  
 <span data-ttu-id="5aa36-116">[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] サーバーの照合順序プロパティは変更できません。</span><span class="sxs-lookup"><span data-stu-id="5aa36-116">The [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] server collation property cannot be changed.</span></span> <span data-ttu-id="5aa36-117">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] のアップグレードを完了できなくなります。</span><span class="sxs-lookup"><span data-stu-id="5aa36-117">You will not be able to complete an upgrade of [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span> <span data-ttu-id="5aa36-118">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] インストールを、互換性のあるサーバー照合順序を使用している新しいサーバーに移行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5aa36-118">You will need to migrate your [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] installation to a new server which is using a compatible server collation.</span></span> <span data-ttu-id="5aa36-119">詳細については、「</span><span class="sxs-lookup"><span data-stu-id="5aa36-119">For more information, see the following:</span></span>  
  
-   [<span data-ttu-id="5aa36-120">Reporting Services のアップグレードと移行</span><span class="sxs-lookup"><span data-stu-id="5aa36-120">Upgrade and Migrate Reporting Services</span></span>](https://go.microsoft.com/fwlink/?LinkId=233227)  
  
-   [<span data-ttu-id="5aa36-121">SQL Server 照合順序の選択</span><span class="sxs-lookup"><span data-stu-id="5aa36-121">Selecting a SQL Server Collation</span></span>](https://go.microsoft.com/fwlink/?LinkId=233226)  
  
  
