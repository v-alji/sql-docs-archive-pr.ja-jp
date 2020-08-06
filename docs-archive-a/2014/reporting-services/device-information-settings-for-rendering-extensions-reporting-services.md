---
title: 表示拡張機能のデバイス情報設定 (Reporting Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 947b0ee1-bb35-4b4e-9527-dc501566e7d1
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: f15e27e01cd43bafda3aede3deca7729f2c89756
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87719659"
---
# <a name="device-information-settings-for-rendering-extensions-reporting-services"></a><span data-ttu-id="837c4-102">表示拡張機能のデバイス情報設定 (Reporting Services)</span><span class="sxs-lookup"><span data-stu-id="837c4-102">Device Information Settings for Rendering Extensions (Reporting Services)</span></span>
  <span data-ttu-id="837c4-103">[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]では、デバイス情報設定を使用して、表示パラメーターを表示拡張機能に渡します。</span><span class="sxs-lookup"><span data-stu-id="837c4-103">In [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)], device information settings are used to pass rendering parameters to a rendering extension.</span></span> <span data-ttu-id="837c4-104">各表示拡張機能では、特定の設定セットを使用できます。</span><span class="sxs-lookup"><span data-stu-id="837c4-104">Each rendering extension accepts a specific set of settings.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="837c4-105">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="837c4-105">In This Section</span></span>  
  
|<span data-ttu-id="837c4-106">トピック</span><span class="sxs-lookup"><span data-stu-id="837c4-106">Topic</span></span>|<span data-ttu-id="837c4-107">説明</span><span class="sxs-lookup"><span data-stu-id="837c4-107">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="837c4-108">ATOM デバイス情報設定</span><span class="sxs-lookup"><span data-stu-id="837c4-108">ATOM Device Information Settings</span></span>](../../2014/reporting-services/atom-device-information-settings.md)|<span data-ttu-id="837c4-109">Atom 準拠の表示出力に関連するデバイス情報設定について説明します。</span><span class="sxs-lookup"><span data-stu-id="837c4-109">Describes the device information settings that are associated with Atom compliant rendering output.</span></span>|  
|[<span data-ttu-id="837c4-110">CSV デバイス情報設定</span><span class="sxs-lookup"><span data-stu-id="837c4-110">CSV Device Information Settings</span></span>](csv-device-information-settings.md)|<span data-ttu-id="837c4-111">CSV 表示出力に関連するデバイス情報設定について説明します。</span><span class="sxs-lookup"><span data-stu-id="837c4-111">Describes the device information settings that are associated with CSV rendering output.</span></span>|  
|[<span data-ttu-id="837c4-112">Excel デバイス情報設定</span><span class="sxs-lookup"><span data-stu-id="837c4-112">Excel Device Information Settings</span></span>](excel-device-information-settings.md)|<span data-ttu-id="837c4-113">Excel 表示出力に関連するデバイス情報設定について説明します。</span><span class="sxs-lookup"><span data-stu-id="837c4-113">Describes the device information settings that are associated with Excel rendering output.</span></span>|  
|[<span data-ttu-id="837c4-114">Word デバイス情報設定</span><span class="sxs-lookup"><span data-stu-id="837c4-114">Word Device Information Settings</span></span>](word-device-information-settings.md)|<span data-ttu-id="837c4-115">Word 表示出力に関連するデバイス情報設定について説明します。</span><span class="sxs-lookup"><span data-stu-id="837c4-115">Describes the device information settings that are associated with Word rendering output.</span></span>|  
|[<span data-ttu-id="837c4-116">HTML デバイス情報設定</span><span class="sxs-lookup"><span data-stu-id="837c4-116">HTML Device Information Settings</span></span>](html-device-information-settings.md)|<span data-ttu-id="837c4-117">HTML 表示出力に関連するデバイス情報設定について説明します。</span><span class="sxs-lookup"><span data-stu-id="837c4-117">Describes the device information settings that are associated with HTML rendering output.</span></span>|  
|[<span data-ttu-id="837c4-118">画像デバイス情報設定</span><span class="sxs-lookup"><span data-stu-id="837c4-118">Image Device Information Settings</span></span>](image-device-information-settings.md)|<span data-ttu-id="837c4-119">IMAGE 表示出力に関連するデバイス情報設定について説明します。</span><span class="sxs-lookup"><span data-stu-id="837c4-119">Describes the device information settings that are associated with IMAGE rendering output.</span></span>|  
|[<span data-ttu-id="837c4-120">MHTML デバイス情報設定</span><span class="sxs-lookup"><span data-stu-id="837c4-120">MHTML Device Information Settings</span></span>](mhtml-device-information-settings.md)|<span data-ttu-id="837c4-121">MHTML 表示出力に関連するデバイス情報設定について説明します。</span><span class="sxs-lookup"><span data-stu-id="837c4-121">Describes the device information settings that are associated with MHTML rendering output.</span></span>|  
|[<span data-ttu-id="837c4-122">PDF デバイス情報の設定</span><span class="sxs-lookup"><span data-stu-id="837c4-122">PDF Device Information Settings</span></span>](pdf-device-information-settings.md)|<span data-ttu-id="837c4-123">PDF 表示出力に関連するデバイス情報設定について説明します。</span><span class="sxs-lookup"><span data-stu-id="837c4-123">Describes the device information settings that are associated with PDF rendering output.</span></span>|  
|[<span data-ttu-id="837c4-124">XML デバイス情報設定</span><span class="sxs-lookup"><span data-stu-id="837c4-124">XML Device Information Settings</span></span>](xml-device-information-settings.md)|<span data-ttu-id="837c4-125">XML 表示出力に関連するデバイス情報設定について説明します。</span><span class="sxs-lookup"><span data-stu-id="837c4-125">Describes the device information settings that are associated with XML rendering output.</span></span>|  
|[<span data-ttu-id="837c4-126">RGDI デバイス情報設定</span><span class="sxs-lookup"><span data-stu-id="837c4-126">RGDI Device Information Settings</span></span>](rgdi-device-information-settings.md)|<span data-ttu-id="837c4-127">RGDI 表示出力に関連するデバイス情報設定について説明します。</span><span class="sxs-lookup"><span data-stu-id="837c4-127">Describes the device information settings that are associated with RGDI rendering output.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="837c4-128">参照</span><span class="sxs-lookup"><span data-stu-id="837c4-128">See Also</span></span>  
 [<span data-ttu-id="837c4-129">RSReportServer.Config で表示拡張機能パラメーターをカスタマイズする</span><span class="sxs-lookup"><span data-stu-id="837c4-129">Customize Rendering Extension Parameters in RSReportServer.Config</span></span>](customize-rendering-extension-parameters-in-rsreportserver-config.md)  
  
  
