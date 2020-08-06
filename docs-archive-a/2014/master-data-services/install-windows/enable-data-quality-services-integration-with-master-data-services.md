---
title: マスター データ サービスを使用した Data Quality Services 統合の有効化 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
ms.assetid: ab32938d-a80e-4106-80d4-94b2de3d67dc
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 8d2fa25254cae2a129b6e08ff657d92af4ff9455
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634575"
---
# <a name="enable-data-quality-services-integration-with-master-data-services"></a><span data-ttu-id="022bf-102">マスター データ サービスを使用した Data Quality Services 統合の有効化</span><span class="sxs-lookup"><span data-stu-id="022bf-102">Enable Data Quality Services Integration with Master Data Services</span></span>
  <span data-ttu-id="022bf-103">[!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]では、Data Quality Services (DQS) によって照合機能が提供されます。</span><span class="sxs-lookup"><span data-stu-id="022bf-103">In the [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)], matching functionality is provided by Data Quality Services (DQS).</span></span> <span data-ttu-id="022bf-104">この機能を使用するには、機能を有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="022bf-104">This functionality must be enabled to be used.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="022bf-105">前提条件</span><span class="sxs-lookup"><span data-stu-id="022bf-105">Prerequisites</span></span>  
  
-   <span data-ttu-id="022bf-106">[!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] Web アプリケーションとデータベースが存在する必要があります。</span><span class="sxs-lookup"><span data-stu-id="022bf-106">A [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] web application and database must exist.</span></span>  
  
-   <span data-ttu-id="022bf-107">Data Quality Services 機能と Data Quality クライアントは、MDS データベースをホストする同じ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンス上にインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="022bf-107">The Data Quality Services feature and the Data Quality Client must be installed on the same [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance that hosts the MDS database.</span></span> <span data-ttu-id="022bf-108">詳細については、「 [Data Quality Services のインストール](../../data-quality-services/install-windows/install-data-quality-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="022bf-108">For more information, see [Install Data Quality Services](../../data-quality-services/install-windows/install-data-quality-services.md).</span></span>  
  
### <a name="to-enable-data-quality-services-integration"></a><span data-ttu-id="022bf-109">Data Quality Services 統合を有効にするには</span><span class="sxs-lookup"><span data-stu-id="022bf-109">To enable Data Quality Services integration</span></span>  
  
1.  <span data-ttu-id="022bf-110">[!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)]を開きます。</span><span class="sxs-lookup"><span data-stu-id="022bf-110">Open [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)].</span></span>  
  
2.  <span data-ttu-id="022bf-111">左ペインで **[Web の構成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="022bf-111">In the left pane, click **Web Configuration**.</span></span>  
  
3.  <span data-ttu-id="022bf-112">**[Web の構成]** ページで、Web サイトと Web アプリケーションを選択します。</span><span class="sxs-lookup"><span data-stu-id="022bf-112">On the **Web Configuration** page, select the website and web application.</span></span>  
  
4.  <span data-ttu-id="022bf-113">**[DQS 統合の有効化]** セクションで、 **[Data Quality Services との統合を有効化]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="022bf-113">In the **Enable DQS Integration** section, click **Enable integration with Data Quality Services**.</span></span>  
  
5.  <span data-ttu-id="022bf-114">確認のダイアログ ボックスで **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="022bf-114">On the confirmation dialog box, click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="022bf-115">参照</span><span class="sxs-lookup"><span data-stu-id="022bf-115">See Also</span></span>  
 <span data-ttu-id="022bf-116">[Excel 用 MDS アドインでのデータ品質照合](../microsoft-excel-add-in/data-quality-matching-in-the-mds-add-in-for-excel.md) </span><span class="sxs-lookup"><span data-stu-id="022bf-116">[Data Quality Matching in the MDS Add-in for Excel](../microsoft-excel-add-in/data-quality-matching-in-the-mds-add-in-for-excel.md) </span></span>  
 <span data-ttu-id="022bf-117">[Microsoft Excel 用マスター データ サービス アドイン](../microsoft-excel-add-in/master-data-services-add-in-for-microsoft-excel.md) </span><span class="sxs-lookup"><span data-stu-id="022bf-117">[Master Data Services Add-in for Microsoft Excel](../microsoft-excel-add-in/master-data-services-add-in-for-microsoft-excel.md) </span></span>  
 [<span data-ttu-id="022bf-118">マスター データ サービスのインストール</span><span class="sxs-lookup"><span data-stu-id="022bf-118">Install Master Data Services</span></span>](install-master-data-services.md)  
  
  
