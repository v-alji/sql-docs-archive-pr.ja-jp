---
title: Azure サブスクリプション接続マネージャー | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.afpsubscrconn.f1
- sql11.dts.designer.afpsubscrconn.f1
ms.assetid: e1225327-c308-4c50-8f44-c411f52ef378
author: chugugrace
ms.author: chugu
ms.openlocfilehash: bff1286525983b32c2191f1f8864a0f2bef0e6b0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641186"
---
# <a name="azure-subscription-connection-manager"></a><span data-ttu-id="88dfe-102">Azure サブスクリプション接続マネージャー</span><span class="sxs-lookup"><span data-stu-id="88dfe-102">Azure Subscription Connection Manager</span></span>
  <span data-ttu-id="88dfe-103">Azure HDInsight 接続マネージャーを使用すると、Azure サブスクリプション ID と管理証明書のプロパティに指定した値を使用して、SSIS パッケージを Azure サブスクリプションに接続できます。</span><span class="sxs-lookup"><span data-stu-id="88dfe-103">The Azure HDInsight connection manager enables an SSIS package to connect to an Azure subscription by using the values you specify for the properties: Azure Subscription ID and Management Certificate.</span></span>

1.  <span data-ttu-id="88dfe-104">上記の **[SSIS 接続マネージャーの追加]** ダイアログ ボックスで **[Azure サブスクリプション]** を選択し、 **[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="88dfe-104">In the **Add SSIS Connection Manager** dialog box shown above, you select **Azure Subscription**, and click **Add**.</span></span>  <span data-ttu-id="88dfe-105">次の **[Azure Subscription Connection Manager Editor]** (Azure サブスクリプション接続マネージャー エディター) ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="88dfe-105">You should see the following **Azure Subscription Connection Manager Editor** dialog box.</span></span>

     <span data-ttu-id="88dfe-106">![SSIS-AzureSubscriptionManager](../media/ssis-azuresubscriptionmanager.png "SSIS-AzureSubscriptionManager")</span><span class="sxs-lookup"><span data-stu-id="88dfe-106">![SSIS-AzureSubscriptionManager](../media/ssis-azuresubscriptionmanager.png "SSIS-AzureSubscriptionManager")</span></span>

2.  <span data-ttu-id="88dfe-107">**[Azure サブスクリプション ID]** には、Azure サブスクリプションを一意に識別する Azure サブスクリプション ID を入力します。</span><span class="sxs-lookup"><span data-stu-id="88dfe-107">Enter your Azure subscription ID, which uniquely identifies an Azure subscription, for the **Azure subscription ID**.</span></span>  <span data-ttu-id="88dfe-108">この値は、 [Azure 管理ポータル](https://manage.windowsazure.com) の **[設定]** ページで確認できます。</span><span class="sxs-lookup"><span data-stu-id="88dfe-108">The value can be found on the [Azure Management Portal](https://manage.windowsazure.com) under **Settings** page:</span></span>

     <span data-ttu-id="88dfe-109">![SSIS-AzureSettings-SubscriptionID](../media/ssis-azuresettings-subscriptionid.png "SSIS-AzureSettings-SubscriptionID")</span><span class="sxs-lookup"><span data-stu-id="88dfe-109">![SSIS-AzureSettings-SubscriptionID](../media/ssis-azuresettings-subscriptionid.png "SSIS-AzureSettings-SubscriptionID")</span></span>

3.  <span data-ttu-id="88dfe-110">ドロップダウン リストから **[Management certificate store location (管理証明書ストアの場所)]** と **[Management certificate store name (管理証明書ストアの名前)]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="88dfe-110">Choose **Management certificate store location** and **Management certificate store name** from the drop-down lists.</span></span>

4.  <span data-ttu-id="88dfe-111">**管理証明書の拇印**を入力するか、**[参照]** をクリックして、選択したストアから証明書を選択します。</span><span class="sxs-lookup"><span data-stu-id="88dfe-111">Enter **Management certificate thumbprint** or click the **Browse...** to choose a certificate from the selected store.</span></span> <span data-ttu-id="88dfe-112">証明書は、サブスクリプションの管理証明書としてアップロードする必要があります。</span><span class="sxs-lookup"><span data-stu-id="88dfe-112">The certificate must be uploaded as a management certificate for the subscription.</span></span> <span data-ttu-id="88dfe-113">これを行うには、Azure Portal の次のページで **[アップロード]** をクリックします (詳細については、こちらの [MSDN の投稿](https://msdn.microsoft.com/library/azure/gg551722.aspx)を参照)。</span><span class="sxs-lookup"><span data-stu-id="88dfe-113">To do so, click **Upload** on the following page of the Azure Portal (see this [MSDN post](https://msdn.microsoft.com/library/azure/gg551722.aspx) for more detail).</span></span>

     <span data-ttu-id="88dfe-114">![SSIS-AzureSettings-ManagementCertificate](../media/ssis-azuresettings-managementcertificate.png "SSIS-AzureSettings-ManagementCertificate")</span><span class="sxs-lookup"><span data-stu-id="88dfe-114">![SSIS-AzureSettings-ManagementCertificate](../media/ssis-azuresettings-managementcertificate.png "SSIS-AzureSettings-ManagementCertificate")</span></span>

5.  <span data-ttu-id="88dfe-115">[**接続テスト**] をクリックして接続をテストします。</span><span class="sxs-lookup"><span data-stu-id="88dfe-115">Click **Test Connection** to test the connection.</span></span>

6.  <span data-ttu-id="88dfe-116">**[OK]** をクリックしてダイアログ ボックスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="88dfe-116">Click **OK** to close the dialog box.</span></span>


