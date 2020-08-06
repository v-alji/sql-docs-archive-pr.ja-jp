---
title: Azure Storage 接続マネージャー | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.afpstorageconn.f1
- sql11.dts.designer.afpstorageconn.f1
ms.assetid: 68bd1d04-d20f-4357-a34e-7c9c76457062
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 47580d8d1d961df9fbcbed0bd7164f1c54792b86
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641191"
---
# <a name="azure-storage-connection-manager"></a><span data-ttu-id="e7bb2-102">Azure Storage 接続マネージャー</span><span class="sxs-lookup"><span data-stu-id="e7bb2-102">Azure Storage Connection Manager</span></span>
  <span data-ttu-id="e7bb2-103">Azure Storage 接続マネージャーは、SSIS パッケージがストレージ アカウント名プロパティとアカウント キー プロパティに指定された値を使用して Azure Storage アカウントに接続することを可能にします。</span><span class="sxs-lookup"><span data-stu-id="e7bb2-103">The Azure Storage connection manager enables an SSIS package to connect to an Azure Storage account by using the values you specify for the properties: Storage Account Name and Account Key.</span></span>  
  
1.  <span data-ttu-id="e7bb2-104">**[SSIS 接続マネージャーの追加]** ダイアログ ボックスで **[AzureStorage]**(AzureStorage) を選択し、 **[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e7bb2-104">In the **Add SSIS Connection Manager** dialog box, select **AzureStorage**, and click **Add**.</span></span>  
  
2.  <span data-ttu-id="e7bb2-105">Azure Storage 接続マネージャー エディター ダイアログ ボックスで、インターネット経由で Azure Storage サービスに接続する場合は **[Use Azure account]** (Azure アカウントを使用する) を選択し、Azure Storage エミュレーターによってホストされているローカル サービスに接続する場合は **[Use local developer account]** (ローカル開発者アカウントを使用する) を選択します。</span><span class="sxs-lookup"><span data-stu-id="e7bb2-105">In the Azure Storage Connection Manager Editor dialog box, choose **Use Azure account** to connect to an Azure Storage Service via internet or choose **Use local developer account** to connect to the local service hosted by the Azure Storage Emulator.</span></span>  
  
3.  <span data-ttu-id="e7bb2-106">**[Use Azure account]** (Azure アカウントを使用する) オプションを選択した場合は、次の操作を行います。</span><span class="sxs-lookup"><span data-stu-id="e7bb2-106">If you selected **Use Azure account** option, do the following:</span></span>  
  
    1.  <span data-ttu-id="e7bb2-107">**[Storage account name]** (ストレージ アカウント名) フィールドと **[Account key]** (アカウント キー) フィールドに値を指定します。</span><span class="sxs-lookup"><span data-stu-id="e7bb2-107">Specify values for the **Storage account name** and **Account key** field.</span></span> <span data-ttu-id="e7bb2-108">これらの値は、SSIS パッケージ内で機微なデータとして保存されます。</span><span class="sxs-lookup"><span data-stu-id="e7bb2-108">These values will be stored as sensitive data in SSIS package.</span></span>  
  
    2.  <span data-ttu-id="e7bb2-109">Azure Storage サービスへの接続に HTTP ではなく HTTPS を使用する場合は、 **[Use HTTPS]** (HTTPS を使用する) を選択します。</span><span class="sxs-lookup"><span data-stu-id="e7bb2-109">Select **Use HTTPS** if you want to use HTTPS instead of HTTP to connect to the Azure Storage Service.</span></span>  
  
4.  <span data-ttu-id="e7bb2-110">**[OK]** をクリックしてダイアログ ボックスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="e7bb2-110">Click **OK** to close the dialog box.</span></span>  
  
5.  <span data-ttu-id="e7bb2-111">作成した接続マネージャーのプロパティは、 **[プロパティ]** ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="e7bb2-111">You can see the properties of the connection manager you created in the **Properties** window.</span></span>  
  
  
