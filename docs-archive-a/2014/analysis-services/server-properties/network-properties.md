---
title: ネットワークのプロパティ |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- LingerTimeout property
- EnableNagleAlgorithm property
- MinPendingAcceptExCount property
- MaxPendingSendCount property
- EnableBinaryXML property
- MinPendingReceiveCount property
- MaxCompletedReceiveCount property
- DisableNonblockingMode property
- RequestSizeThreshold property
- CompressionLevel property
- ReceiveBufferSize property
- EnableCompression property
- ServerSendTimeout property
- IPV4Support property
- MaxPendingReceiveCount property
- MaxPendingAcceptExCount property
- IPV6Support property
- MaxAllowedRequestSize property
- ServerReceiveTimeout property
- EnableLingerOnClose property
- InitialConnectTimeout property
- SendBufferSize property
- ScatterReceiveMultiplier property
- network properties [Analysis Services]
ms.assetid: ef4251e2-abe5-4c5b-9868-7549782d0244
author: minewiskan
ms.author: owend
ms.openlocfilehash: 10ad5bbbcffdfc3d3c4fefe3111e4c4425919915
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640271"
---
# <a name="network-properties"></a><span data-ttu-id="c8ac7-102">ネットワーク プロパティ</span><span class="sxs-lookup"><span data-stu-id="c8ac7-102">Network Properties</span></span>
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] <span data-ttu-id="c8ac7-103">では、次の表に示すサーバー プロパティがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="c8ac7-103">supports the server properties listed in the following tables.</span></span> <span data-ttu-id="c8ac7-104">その他のサーバー プロパティとその設定方法の詳細については、「 [Configure Server Properties in Analysis Services](server-properties-in-analysis-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c8ac7-104">For more information about additional server properties and how to set them, see [Configure Server Properties in Analysis Services](server-properties-in-analysis-services.md).</span></span>  
  
 <span data-ttu-id="c8ac7-105">**適用対象:** 多次元サーバー モードおよびテーブル サーバー モード</span><span class="sxs-lookup"><span data-stu-id="c8ac7-105">**Applies to:** Multidimensional and Tabular server mode</span></span>  
  
## <a name="general"></a><span data-ttu-id="c8ac7-106">全般</span><span class="sxs-lookup"><span data-stu-id="c8ac7-106">General</span></span>  
 `ListenOnlyOnLocalConnections`  
 <span data-ttu-id="c8ac7-107">localhost などのローカル接続のみリッスンするかどうかを識別する、ブール型プロパティです。</span><span class="sxs-lookup"><span data-stu-id="c8ac7-107">A Boolean property that identifies whether to listen only on local connections, for example localhost.</span></span>  
  
## <a name="listener"></a><span data-ttu-id="c8ac7-108">リスナー</span><span class="sxs-lookup"><span data-stu-id="c8ac7-108">Listener</span></span>  
 `IPV4Support`  
 <span data-ttu-id="c8ac7-109">IPv4 プロトコルのサポートを定義する、符号付き 32 ビット整数のプロパティです。</span><span class="sxs-lookup"><span data-stu-id="c8ac7-109">A signed 32-bit integer property that defines support for IPv4 protocol.</span></span> <span data-ttu-id="c8ac7-110">このプロパティは、次の表に示すいずれかの値になります。</span><span class="sxs-lookup"><span data-stu-id="c8ac7-110">This property has one of the values listed in the following table:</span></span>  
  
|<span data-ttu-id="c8ac7-111">値</span><span class="sxs-lookup"><span data-stu-id="c8ac7-111">Value</span></span>|<span data-ttu-id="c8ac7-112">説明</span><span class="sxs-lookup"><span data-stu-id="c8ac7-112">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="c8ac7-113">*0*</span><span class="sxs-lookup"><span data-stu-id="c8ac7-113">*0*</span></span>|<span data-ttu-id="c8ac7-114">IPv4 は無効です。クライアントは接続できません。</span><span class="sxs-lookup"><span data-stu-id="c8ac7-114">IPv4 disabled; clients can't connect.</span></span>|  
|<span data-ttu-id="c8ac7-115">*1*</span><span class="sxs-lookup"><span data-stu-id="c8ac7-115">*1*</span></span>|<span data-ttu-id="c8ac7-116">(既定) IPv4 が必要です。IPv4 をリッスンできない場合、サーバーは起動しません。</span><span class="sxs-lookup"><span data-stu-id="c8ac7-116">(Default) IPv4 is required; server won't start if it cannot listen to IPv4.</span></span>|  
|<span data-ttu-id="c8ac7-117">*2*</span><span class="sxs-lookup"><span data-stu-id="c8ac7-117">*2*</span></span>|<span data-ttu-id="c8ac7-118">IPv4 はオプションです。サーバーは IPv4 をリッスンしようとしますが、それが不可能でも起動します。</span><span class="sxs-lookup"><span data-stu-id="c8ac7-118">IPv4 is optional; server tries to listen to IPv4 but starts even if unable to.</span></span>|  
  
 `IPV6Support`  
 <span data-ttu-id="c8ac7-119">IPv6 プロトコルのサポートを定義する、符号付き 32 ビット整数のプロパティです。</span><span class="sxs-lookup"><span data-stu-id="c8ac7-119">A signed 32-bit integer property that defines support for IPv6 protocol.</span></span> <span data-ttu-id="c8ac7-120">このプロパティは、次の表に示すいずれかの値になります。</span><span class="sxs-lookup"><span data-stu-id="c8ac7-120">This property has one of the values listed in the following table:</span></span>  
  
|<span data-ttu-id="c8ac7-121">値</span><span class="sxs-lookup"><span data-stu-id="c8ac7-121">Value</span></span>|<span data-ttu-id="c8ac7-122">説明</span><span class="sxs-lookup"><span data-stu-id="c8ac7-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="c8ac7-123">*0*</span><span class="sxs-lookup"><span data-stu-id="c8ac7-123">*0*</span></span>|<span data-ttu-id="c8ac7-124">IPv6 は無効です。クライアントは接続できません。</span><span class="sxs-lookup"><span data-stu-id="c8ac7-124">IPv6 disabled; clients can't connect.</span></span>|  
|<span data-ttu-id="c8ac7-125">*1*</span><span class="sxs-lookup"><span data-stu-id="c8ac7-125">*1*</span></span>|<span data-ttu-id="c8ac7-126">(既定) IPv6 が必要です。IPv6 をリッスンできない場合、サーバーは起動しません。</span><span class="sxs-lookup"><span data-stu-id="c8ac7-126">(Default) IPv6 is required; server won't start if it cannot listen to IPv6.</span></span>|  
|<span data-ttu-id="c8ac7-127">*2*</span><span class="sxs-lookup"><span data-stu-id="c8ac7-127">*2*</span></span>|<span data-ttu-id="c8ac7-128">IPv6 はオプションです。サーバーは IPv6 をリッスンしようとしますが、それが不可能でも起動します。</span><span class="sxs-lookup"><span data-stu-id="c8ac7-128">IPv6 is optional; server tries to listen to IPv6 but starts even if unable to.</span></span>|  
  
 `MaxAllowedRequestSize`  
 <span data-ttu-id="c8ac7-129">詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="c8ac7-129">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `RequestSizeThreshold`  
 <span data-ttu-id="c8ac7-130">詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="c8ac7-130">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `ServerReceiveTimeout`  
 <span data-ttu-id="c8ac7-131">詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="c8ac7-131">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `ServerSendTimeout`  
 <span data-ttu-id="c8ac7-132">詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="c8ac7-132">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
## <a name="requests"></a><span data-ttu-id="c8ac7-133">Requests</span><span class="sxs-lookup"><span data-stu-id="c8ac7-133">Requests</span></span>  
 `EnableBinaryXML`  
 <span data-ttu-id="c8ac7-134">サーバーがバイナリ XML 形式の要求を認識するかどうかを指定する、ブール型プロパティです。</span><span class="sxs-lookup"><span data-stu-id="c8ac7-134">A Boolean property that specifies whether the server will recognize requests binary xml format.</span></span>  
  
 `EnableCompression`  
 <span data-ttu-id="c8ac7-135">要求の圧縮を有効にするかどうかを指定する、ブール型プロパティです。</span><span class="sxs-lookup"><span data-stu-id="c8ac7-135">A Boolean property that specifies whether compression is enabled for requests.</span></span>  
  
## <a name="responses"></a><span data-ttu-id="c8ac7-136">Responses</span><span class="sxs-lookup"><span data-stu-id="c8ac7-136">Responses</span></span>  
 `CompressionLevel`  
 <span data-ttu-id="c8ac7-137">詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="c8ac7-137">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `EnableBinaryXML`  
 <span data-ttu-id="c8ac7-138">サーバーでバイナリ XML 応答を有効にするかどうかを指定する、ブール型プロパティです。</span><span class="sxs-lookup"><span data-stu-id="c8ac7-138">A Boolean property that specifies whether the server is enabled for binary xml responses.</span></span>  
  
 `EnableCompression`  
 <span data-ttu-id="c8ac7-139">クライアント要求に対する応答の圧縮を有効にするかどうかを指定する、ブール型プロパティです。</span><span class="sxs-lookup"><span data-stu-id="c8ac7-139">A Boolean property that specifies whether compression is enabled for responses to client requests.</span></span>  
  
## <a name="tcp"></a><span data-ttu-id="c8ac7-140">TCP</span><span class="sxs-lookup"><span data-stu-id="c8ac7-140">TCP</span></span>  
 `InitialConnectTimeout`  
 <span data-ttu-id="c8ac7-141">詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="c8ac7-141">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `MaxCompletedReceiveCount`  
 <span data-ttu-id="c8ac7-142">詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="c8ac7-142">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `MaxPendingAcceptExCount`  
 <span data-ttu-id="c8ac7-143">詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="c8ac7-143">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `MaxPendingReceiveCount`  
 <span data-ttu-id="c8ac7-144">詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="c8ac7-144">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `MaxPendingSendCount`  
 <span data-ttu-id="c8ac7-145">詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="c8ac7-145">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `MinPendingAcceptExCount`  
 <span data-ttu-id="c8ac7-146">詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="c8ac7-146">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `MinPendingReceiveCount`  
 <span data-ttu-id="c8ac7-147">詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="c8ac7-147">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `ScatterReceiveMultiplier`  
 <span data-ttu-id="c8ac7-148">詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="c8ac7-148">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `SocketOptions\ DisableNonblockingMode`  
 <span data-ttu-id="c8ac7-149">詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="c8ac7-149">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `SocketOptions\ EnableLingerOnClose`  
 <span data-ttu-id="c8ac7-150">詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="c8ac7-150">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `SocketOptions\EnableNagleAlgorithm`  
 <span data-ttu-id="c8ac7-151">詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="c8ac7-151">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `SocketOptions\ LingerTimeout`  
 <span data-ttu-id="c8ac7-152">詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="c8ac7-152">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `SocketOptions\ ReceiveBufferSize`  
 <span data-ttu-id="c8ac7-153">詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="c8ac7-153">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `SocketOptions\ SendBufferSize`  
 <span data-ttu-id="c8ac7-154">詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="c8ac7-154">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8ac7-155">参照</span><span class="sxs-lookup"><span data-stu-id="c8ac7-155">See Also</span></span>  
 <span data-ttu-id="c8ac7-156">[Analysis Services でのサーバープロパティの構成](server-properties-in-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="c8ac7-156">[Configure Server Properties in Analysis Services](server-properties-in-analysis-services.md) </span></span>  
 [<span data-ttu-id="c8ac7-157">Analysis Services インスタンスのサーバー モードの決定</span><span class="sxs-lookup"><span data-stu-id="c8ac7-157">Determine the Server Mode of an Analysis Services Instance</span></span>](../instances/determine-the-server-mode-of-an-analysis-services-instance.md)  
  
  
