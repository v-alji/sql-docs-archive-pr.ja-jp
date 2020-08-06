---
title: Azure HDInsight 接続マネージャー | Microsoft Docs
ms.custom: ''
ms.date: 02/28/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- SQL12.DTS.DESIGNER.AFPHDICM.F1
- SQL11.DTS.DESIGNER.AFPHDICM.F1
ms.assetid: 850a978d-5dba-45b6-a10e-306aafbc353d
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 0eaf2f57fec50a58ad1b7e7578407fb6cf3fa0c0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87712330"
---
# <a name="azure-hdinsight-connection-manager"></a><span data-ttu-id="861fd-102">Azure HDInsight 接続マネージャー</span><span class="sxs-lookup"><span data-stu-id="861fd-102">Azure HDInsight Connection Manager</span></span>
<span data-ttu-id="861fd-103">**Azure HDInsight 接続マネージャー**により、SSIS パッケージは Azure HDInsight クラスターに接続できます。</span><span class="sxs-lookup"><span data-stu-id="861fd-103">The **Azure HDInsight Connection Manager** enables an SSIS package to connect to an Azure HDInsight cluster.</span></span>

<span data-ttu-id="861fd-104">**Azure HDInsight 接続マネージャー**を作成して構成するには、以下の手順のようにします。</span><span class="sxs-lookup"><span data-stu-id="861fd-104">To create and configure an **Azure HDInsight Connection Manager**, follow the steps below:</span></span>

1. <span data-ttu-id="861fd-105">**[SSIS 接続マネージャーの追加]** ダイアログ ボックスで **[AzureHDInsight]** を選び、**[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="861fd-105">In the **Add SSIS Connection Manager** dialog box, select **AzureHDInsight**, and click **Add**.</span></span>
2. <span data-ttu-id="861fd-106">**[Azure HDInsight Connection Manager Editor]\(Azure HDInsight 接続マネージャー エディター\)** ダイアログ ボックスで、接続先の HDInsight クラスターの **[Cluster DNS name]\(クラスター DNS 名\)** (プロトコル プレフィックスなし)、**[ユーザー名]**、**[パスワード]** を指定します。</span><span class="sxs-lookup"><span data-stu-id="861fd-106">In the **Azure HDInsight Connection Manager Editor** dialog box, specify the **Cluster DNS name** (without the protocol prefix), **Username**, and **Password** for the HDInsight cluster to connect to.</span></span>
3. <span data-ttu-id="861fd-107">**[OK]** をクリックしてダイアログ ボックスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="861fd-107">Click **OK** to close the dialog box.</span></span>
4. <span data-ttu-id="861fd-108">作成した接続マネージャーのプロパティは、 **[プロパティ]** ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="861fd-108">You can see the properties of the connection manager you created in the **Properties** window.</span></span>
