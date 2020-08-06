---
title: Azure Resource Manager 接続マネージャー | Microsoft Docs
ms.custom: ''
ms.date: 02/28/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- SQL12.DTS.DESIGNER.AFPARMCM.F1
- SQL11.DTS.DESIGNER.AFPARMCM.F1
ms.assetid: a2380258-0418-4a8c-a731-5071a44ddf1e
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 1dce4def11f14072295dbf3cde9d5ab77304fe74
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641839"
---
# <a name="azure-resource-manager-connection-manager"></a><span data-ttu-id="7153a-102">Azure Resource Manager 接続マネージャー</span><span class="sxs-lookup"><span data-stu-id="7153a-102">Azure Resource Manager Connection Manager</span></span>
<span data-ttu-id="7153a-103">**Azure Resource Manager 接続マネージャー**により、SSIS パッケージは[サービス プリンシパル](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-create-service-principal-portal)を使って Azure リソースを管理できます。</span><span class="sxs-lookup"><span data-stu-id="7153a-103">The **Azure Resource Manager Connection Manager** enables an SSIS package to manage Azure resources using a [service principal](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-create-service-principal-portal).</span></span>

<span data-ttu-id="7153a-104">**Azure Resource Manager 接続マネージャー**を作成して構成するには、以下の手順のようにします。</span><span class="sxs-lookup"><span data-stu-id="7153a-104">To create and configure an **Azure Resource Manager Connection Manager**, follow the steps below:</span></span>

1. <span data-ttu-id="7153a-105">**[SSIS 接続マネージャーの追加]** ダイアログ ボックスで **[AzureResourceManager]** を選び、**[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7153a-105">In the **Add SSIS Connection Manager** dialog box, select **AzureResourceManager**, and click **Add**.</span></span>
2. <span data-ttu-id="7153a-106">**[Azure Resource Manager Connection Manager Editor]\(Azure Resource Manager 接続マネージャー エディター\)** ダイアログ ボックスで、サービス プリンシパルの **[Application ID]\(アプリケーション ID\)**、**[Application Key]\(アプリケーション キー\)**、**[Tenant ID]\(テナント ID\)** を指定します。</span><span class="sxs-lookup"><span data-stu-id="7153a-106">In the **Azure Resource Manager Connection Manager Editor** dialog box, specify the **Application ID**, **Application Key**, and **Tenant ID** for the service principal.</span></span> <span data-ttu-id="7153a-107">これらのプロパティについて詳しくは、[こちら](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-create-service-principal-portal)の記事をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="7153a-107">For details about these properties, please refer to [this](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-create-service-principal-portal) article.</span></span>
3. <span data-ttu-id="7153a-108">**[OK]** をクリックしてダイアログ ボックスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="7153a-108">Click **OK** to close the dialog box.</span></span>
4. <span data-ttu-id="7153a-109">作成した接続マネージャーのプロパティは、 **[プロパティ]** ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="7153a-109">You can see the properties of the connection manager you created in the **Properties** window.</span></span>
