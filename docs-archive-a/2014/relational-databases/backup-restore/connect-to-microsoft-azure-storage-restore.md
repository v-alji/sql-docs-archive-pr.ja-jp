---
title: Azure Storage への接続 (復元) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
f1_keywords:
- sql12.swb.restore.connectstorage.f1
ms.assetid: c0b7d7c8-b878-4b7f-8120-d0c6917b583f
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: dff9730d6592381b1c8e8a1cf7ee45ad7532a440
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645676"
---
# <a name="connect-to-azure-storage-restore"></a><span data-ttu-id="3a98e-102">Azure Storage への接続 (復元)</span><span class="sxs-lookup"><span data-stu-id="3a98e-102">Connect to Azure Storage (Restore)</span></span>
  <span data-ttu-id="3a98e-103">このダイアログ ボックスを使用すると、Azure ストレージ アカウントのファイル ストレージを取得するために、Azure ストレージ アカウント情報への接続を指定できます。</span><span class="sxs-lookup"><span data-stu-id="3a98e-103">The dialog box allows you to specify the connection to Azure storage account information in order to retrieve the files storage in the Azure storage account.</span></span> <span data-ttu-id="3a98e-104">必要な情報を指定した後、 **[接続]** をクリックして Azure Storage への接続を確立します。</span><span class="sxs-lookup"><span data-stu-id="3a98e-104">After specifying the required information, click **Connect** to establish the connection to Azure storage.</span></span>  
  
## <a name="azure-storage-account"></a><span data-ttu-id="3a98e-105">Azure Storage アカウント</span><span class="sxs-lookup"><span data-stu-id="3a98e-105">Azure Storage Account</span></span>  
 <span data-ttu-id="3a98e-106">**ストレージ アカウント**</span><span class="sxs-lookup"><span data-stu-id="3a98e-106">**Storage account**</span></span>  
 <span data-ttu-id="3a98e-107">使用する Azure ストレージ アカウントの名前を選択、入力、または貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="3a98e-107">Select, type or paste the name of the Azure storage account you want to use.</span></span> <span data-ttu-id="3a98e-108">ドロップダウン リストに、以前に使用したアカウントが表示されます。</span><span class="sxs-lookup"><span data-stu-id="3a98e-108">The drop down box lists the accounts previously used.</span></span>  
  
 <span data-ttu-id="3a98e-109">**アカウント キー**</span><span class="sxs-lookup"><span data-stu-id="3a98e-109">**Account key**</span></span>  
 <span data-ttu-id="3a98e-110">Azure ストレージ アカウントのアクセス キーを指定します。</span><span class="sxs-lookup"><span data-stu-id="3a98e-110">Specify the Azure storage account access key.</span></span>  
  
 <span data-ttu-id="3a98e-111">**[安全なエンドポイントを使用する (HTTPS)]** チェック ボックス</span><span class="sxs-lookup"><span data-stu-id="3a98e-111">**Use secure endpoints (HTTPS)** check box</span></span>  
 <span data-ttu-id="3a98e-112">Azure Storage に対してセキュリティで保護された接続を確立するには、このオプションを選択します (推奨)。</span><span class="sxs-lookup"><span data-stu-id="3a98e-112">Select this option to make a secure connection to Azure storage - recommended.</span></span>  
  
 <span data-ttu-id="3a98e-113">**[アカウント キーを保存する]** チェック ボックス</span><span class="sxs-lookup"><span data-stu-id="3a98e-113">**Save account key** check box</span></span>  
 <span data-ttu-id="3a98e-114">このストレージ アカウントのアクセス キーを SQL Server に記憶させる場合は、このチェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="3a98e-114">Select this check box if you want SQL Server to remember the access key for this storage account.</span></span>  
  
### <a name="sql-credential"></a><span data-ttu-id="3a98e-115">[SQL 資格情報]</span><span class="sxs-lookup"><span data-stu-id="3a98e-115">SQL Credential</span></span>  
 <span data-ttu-id="3a98e-116">**[既存の資格情報の選択]**</span><span class="sxs-lookup"><span data-stu-id="3a98e-116">**Select an existing credential**</span></span>  
 <span data-ttu-id="3a98e-117">ストレージ アカウントおよびアカウント キー情報と一致する既存の SQL 資格情報を選択します。</span><span class="sxs-lookup"><span data-stu-id="3a98e-117">Select an existing SQL Credential that matches the storage account and account key information.</span></span>  
  
 <span data-ttu-id="3a98e-118">**[新しい資格情報の作成]**</span><span class="sxs-lookup"><span data-stu-id="3a98e-118">**Create a new Credential**</span></span>  
 <span data-ttu-id="3a98e-119">ストレージ アカウントとアカウント キー情報を使用して新しい資格情報を作成するには、このオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="3a98e-119">Select this option to create a new credential using the storage account and account key information.</span></span> <span data-ttu-id="3a98e-120">**[資格情報名]** フィールドに新しい資格情報の名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="3a98e-120">Specify the name of the new credential in the **Credential Name** field.</span></span>  
  
  
