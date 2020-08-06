---
title: 資格情報の作成- Azure ストレージに対する認証 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
f1_keywords:
- sql12.swb.backuptourl.createcred.f1
ms.assetid: 0622619d-27c5-4ff0-83e5-cde31648c27a
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: afdbf2647c79e07cf3f190ec6710eeb6b7718f6c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740074"
---
# <a name="create-credential---authenticate-to-azure-storage"></a><span data-ttu-id="85f26-102">資格情報の作成- Azure ストレージに対する認証</span><span class="sxs-lookup"><span data-stu-id="85f26-102">Create Credential - Authenticate to Azure Storage</span></span>
  <span data-ttu-id="85f26-103">**[Backup To URL - 資格情報の作成]** ダイアログ ボックスを使用すると、新しい SQL 資格情報を作成できます。</span><span class="sxs-lookup"><span data-stu-id="85f26-103">Use the **Backup to URL - Create Credential** dialog box to create a new SQL Credential.</span></span>  
  
 <span data-ttu-id="85f26-104">このダイアログ ボックスを使用して資格情報を作成する場合、サブスクリプションとストレージ アカウント情報を検証するために、ローカル証明書ストアに追加した Azure 管理証明書、またはコンピューターにダウンロードした公開プロファイルを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="85f26-104">When using this dialog box to create a credential, you must provide an Azure Management Certificate added to the local certificate store or a publishing profile downloaded to your computer to validate the subscription and the storage account information.</span></span>  
  
 <span data-ttu-id="85f26-105">**[SQL 資格情報]**</span><span class="sxs-lookup"><span data-stu-id="85f26-105">**SQL Credential**</span></span>  
 <span data-ttu-id="85f26-106">作成する SQL 資格情報の名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="85f26-106">Specify the name of the SQL Credential you want to create.</span></span>  
  
## <a name="azure-credentials"></a><span data-ttu-id="85f26-107">Azure 資格情報</span><span class="sxs-lookup"><span data-stu-id="85f26-107">Azure Credentials</span></span>  
 <span data-ttu-id="85f26-108">**[管理証明書]**</span><span class="sxs-lookup"><span data-stu-id="85f26-108">**Management Certificate**</span></span>  
 <span data-ttu-id="85f26-109">このオプションを使用して、Azure からの管理証明書に一致するローカル証明書ストアの証明書を指定します。</span><span class="sxs-lookup"><span data-stu-id="85f26-109">Use this option to specify a certificate from the local certificate store that matches the management certificate from Azure.</span></span> <span data-ttu-id="85f26-110">Azure 管理証明書の詳細については、「[Azure の管理証明書の作成とアップロード](https://go.microsoft.com/fwlink/?LinkId=320781)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="85f26-110">For more information on Azure management certificate, see [Create and Upload a Management Certificate for Azure](https://go.microsoft.com/fwlink/?LinkId=320781).</span></span>  
  
 <span data-ttu-id="85f26-111">**サブスクリプション**</span><span class="sxs-lookup"><span data-stu-id="85f26-111">**Subscription**</span></span>  
 <span data-ttu-id="85f26-112">ローカル証明書ストアの管理証明書と一致する Azure サブスクリプション ID を選択、入力、または貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="85f26-112">Select, type, or paste your Azure subscription ID that matches the management certificate from the local certificate store.</span></span>  
  
 <span data-ttu-id="85f26-113">**[公開プロファイル]**</span><span class="sxs-lookup"><span data-stu-id="85f26-113">**Publishing Profile**</span></span>  
 <span data-ttu-id="85f26-114">コンピューターにダウンロードした公開プロファイルがある場合は、このオプションを使用します。</span><span class="sxs-lookup"><span data-stu-id="85f26-114">Use this option if you have a publishing profile downloaded to your computer.</span></span> <span data-ttu-id="85f26-115">このオプションを使用すると、サブスクリプション ID と証明書が自動的に入力されます。</span><span class="sxs-lookup"><span data-stu-id="85f26-115">If you use this option, the subscription ID, and the certificate are auto populated.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="85f26-116">SQL Server では現在、公開プロファイルのバージョン 2.0 がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="85f26-116">SQL Server currently supports publishing profile version 2.0.</span></span> <span data-ttu-id="85f26-117">公開プロファイルのサポート対象バージョンをダウンロードするには、「 [公開プロファイルのバージョン 2.0 のダウンロード](https://go.microsoft.com/fwlink/?LinkId=396421)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="85f26-117">To download the supported version of the publishing profile, see [Download Publishing Profile 2.0](https://go.microsoft.com/fwlink/?LinkId=396421).</span></span>  
  
## <a name="storage-account"></a><span data-ttu-id="85f26-118">ストレージ アカウント</span><span class="sxs-lookup"><span data-stu-id="85f26-118">Storage Account</span></span>  
 <span data-ttu-id="85f26-119">バックアップ ファイルを格納するために使用するストレージ アカウントを選択します。</span><span class="sxs-lookup"><span data-stu-id="85f26-119">Select the storage account you want to use to store the backup files on.</span></span>  
  
  
