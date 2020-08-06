---
title: 'レッスン 1: Azure Storage オブジェクトを作成する |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
ms.assetid: 74edd1fd-ab00-46f7-9e29-7ba3f1a446c5
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: d46c6d22ffd92dbf8035bff140960af8ef56122d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632854"
---
# <a name="lesson-1-create-azure-storage-objects"></a><span data-ttu-id="b2ba3-102">レッスン 1:Azure Storage オブジェクトの作成</span><span class="sxs-lookup"><span data-stu-id="b2ba3-102">Lesson 1: Create Azure Storage Objects</span></span>
  <span data-ttu-id="b2ba3-103">クラウド記憶域に [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] バックアップを作成する前に、まず、ストレージ アカウントを作成してから BLOB コンテナーを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b2ba3-103">Before you can create [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] backups on cloud storage, you must first create a storage account, and then a blob container.</span></span> <span data-ttu-id="b2ba3-104">レッスン1では、Azure 管理ポータルにログインし、ストレージアカウントと blob コンテナーを作成する手順について説明します。</span><span class="sxs-lookup"><span data-stu-id="b2ba3-104">Lesson 1 walks you through the steps of Logging into the Azure Management Portal, creating a storage account and a blob container.</span></span>  
  
## <a name="create-a-storage-account"></a><span data-ttu-id="b2ba3-105">ストレージ アカウントを作成する</span><span class="sxs-lookup"><span data-stu-id="b2ba3-105">Create a storage Account</span></span>  
 <span data-ttu-id="b2ba3-106">Azure 管理ポータルからストレージアカウントを作成するには、次の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="b2ba3-106">To create a storage account from the Azure Management Portal, use the following steps:</span></span>  
  
1.  <span data-ttu-id="b2ba3-107">アカウントを使用して Azure 管理ポータルにログインします。</span><span class="sxs-lookup"><span data-stu-id="b2ba3-107">Log in to the Azure Management Portal using your account.</span></span> <span data-ttu-id="b2ba3-108">Azure アカウントをお持ちでない場合は、 [azure の3か月間の無料試用版](https://go.microsoft.com/fwlink/?LinkId=271927)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="b2ba3-108">If you do not have an Azure account, [visit Azure 3-Month free trial](https://go.microsoft.com/fwlink/?LinkId=271927).</span></span>  
  
     <span data-ttu-id="b2ba3-109">![Azure ログイン画面](../../2014/tutorials/media/windowazurelogin-backuptocloud.gif "Azure ログイン画面")</span><span class="sxs-lookup"><span data-stu-id="b2ba3-109">![Azure Login Screen](../../2014/tutorials/media/windowazurelogin-backuptocloud.gif "Azure Login Screen")</span></span>  
  
2.  <span data-ttu-id="b2ba3-110">ストレージアカウントを作成する詳細な手順については、[こちら](https://go.microsoft.com/fwlink/?LinkId=271926)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b2ba3-110">Use the step by step instructions detailed [here](https://go.microsoft.com/fwlink/?LinkId=271926), to create a storage account.</span></span>  
  
3.  <span data-ttu-id="b2ba3-111">前の手順で作成したストレージ アカウントを参照します。</span><span class="sxs-lookup"><span data-stu-id="b2ba3-111">Browse to the storage account you created in previous step.</span></span> <span data-ttu-id="b2ba3-112">Web ページの下部中央にある [キーの**管理**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b2ba3-112">From the bottom center of the web page, click **MANAGE KEYS**.</span></span> <span data-ttu-id="b2ba3-113">アカウント情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="b2ba3-113">The account information is displayed.</span></span> <span data-ttu-id="b2ba3-114">ストレージ アカウント名とアクセス キーをコピーします。</span><span class="sxs-lookup"><span data-stu-id="b2ba3-114">Copy the storage account name, and the Access Keys.</span></span> <span data-ttu-id="b2ba3-115">この情報は、SQL の保存された資格情報を作成するために必要です。</span><span class="sxs-lookup"><span data-stu-id="b2ba3-115">This information is required to create SQL Stored Credentials.</span></span> [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] <span data-ttu-id="b2ba3-116">は、この情報を使用し、ストレージ アカウントにアクセスしてバックアップを作成します。</span><span class="sxs-lookup"><span data-stu-id="b2ba3-116">uses this information to access the storage account and create backups.</span></span>  
  
     <span data-ttu-id="b2ba3-117">![Azure Storage アカウントキーのスクリーンショット](../../2014/tutorials/media/manageaccesskeys-backuptocloud.gif "Azure Storage アカウントキーのスクリーンショット")</span><span class="sxs-lookup"><span data-stu-id="b2ba3-117">![Screen shot of Azure Storage Account Keys](../../2014/tutorials/media/manageaccesskeys-backuptocloud.gif "Screen shot of Azure Storage Account Keys")</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="b2ba3-118">ストレージ アカウントは、REST API を使用してプログラムで作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="b2ba3-118">You can also create a storage account programmatically using REST APIs.</span></span> <span data-ttu-id="b2ba3-119">詳細については、「[ストレージアカウントの作成](https://go.microsoft.com/fwlink/?LinkId=271928)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b2ba3-119">For more information, see [Create Storage Account](https://go.microsoft.com/fwlink/?LinkId=271928).</span></span>  
  
### <a name="create-a-blob-container"></a><span data-ttu-id="b2ba3-120">BLOB コンテナーの作成</span><span class="sxs-lookup"><span data-stu-id="b2ba3-120">Create a Blob Container</span></span>  
 <span data-ttu-id="b2ba3-121">コンテナーには、一連の BLOB をグループ化するコンテナーが用意されています。</span><span class="sxs-lookup"><span data-stu-id="b2ba3-121">A container provides a grouping of a set of blobs.</span></span> <span data-ttu-id="b2ba3-122">すべての BLOB は 1 つのコンテナーに存在する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b2ba3-122">All blobs must be in a container.</span></span> <span data-ttu-id="b2ba3-123">アカウントには、コンテナーを無制限に含めることができますが、少なくとも 1 つのコンテナーが必要です。</span><span class="sxs-lookup"><span data-stu-id="b2ba3-123">An account can contain an unlimited number of containers, but must have at least one container.</span></span> <span data-ttu-id="b2ba3-124">コンテナーには、BLOB を無制限に格納できます。</span><span class="sxs-lookup"><span data-stu-id="b2ba3-124">A container can store an unlimited number of blobs.</span></span>  
  
 <span data-ttu-id="b2ba3-125">コンテナーを作成するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="b2ba3-125">To create a Container, use the following steps:</span></span>  
  
1.  <span data-ttu-id="b2ba3-126">ストレージアカウントを選択し、[**コンテナー** ] タブをクリックし、画面の下部にある [**コンテナーの追加**] をクリックして、新しいダイアログボックスを開きます。</span><span class="sxs-lookup"><span data-stu-id="b2ba3-126">Select the storage account, click the **CONTAINERS** tab and click **ADD CONTAINER** at the bottom of the screen which opens a new dialog box.</span></span>  
  
     <span data-ttu-id="b2ba3-127">![Management Portal でのコンテナーの作成](../../2014/tutorials/media/backuptocloud.gif "Management Portal でのコンテナーの作成")</span><span class="sxs-lookup"><span data-stu-id="b2ba3-127">![Creating a Container in the Management Portal](../../2014/tutorials/media/backuptocloud.gif "Creating a Container in the Management Portal")</span></span>  
  
2.  <span data-ttu-id="b2ba3-128">コンテナーの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="b2ba3-128">Enter the name for the container.</span></span> <span data-ttu-id="b2ba3-129">指定したコンテナー名をメモします。</span><span class="sxs-lookup"><span data-stu-id="b2ba3-129">Make a note of the container name you specified.</span></span> <span data-ttu-id="b2ba3-130">この情報は、レッスン 3 と 4 の T-SQL ステートメントの URL (バックアップ ファイルのパス) で使用されます。</span><span class="sxs-lookup"><span data-stu-id="b2ba3-130">This information is used in the URL (path to backup file) in the T-SQL statements in lesson 3 and 4.</span></span>  
  
3.  <span data-ttu-id="b2ba3-131">[アクセスの**種類**] で [プライベート] を選択します。</span><span class="sxs-lookup"><span data-stu-id="b2ba3-131">Select Private for **Access Type**.</span></span> <span data-ttu-id="b2ba3-132">バックアップ ファイルをセキュリティで保護するためのプライベート コンテナーを作成することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="b2ba3-132">We recommend creating private containers for securing your backup files.</span></span>  
  
     <span data-ttu-id="b2ba3-133">![新しい BLOB コンテナーの作成:](../../2014/tutorials/media/backuptocloud-newblobcontainer.gif "新しい BLOB コンテナーの作成:")</span><span class="sxs-lookup"><span data-stu-id="b2ba3-133">![Creating a new blob container](../../2014/tutorials/media/backuptocloud-newblobcontainer.gif "Creating a new blob container")</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="b2ba3-134">ストレージ アカウントへの認証は、パブリック コンテナーの作成を選択した場合でも、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のバックアップと復元に必要です。</span><span class="sxs-lookup"><span data-stu-id="b2ba3-134">Authentication to the storage account is required for [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] backup and restore even if you choose to create a public container.</span></span>  
    >   
    >  <span data-ttu-id="b2ba3-135">コンテナーは、REST API を使用してプログラムで作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="b2ba3-135">You can also create a container programmatically using REST APIs.</span></span> <span data-ttu-id="b2ba3-136">詳細については、[コンテナーの作成](https://go.microsoft.com/fwlink/?LinkId=271946)に関する説明を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b2ba3-136">For more information, see [Create Container](https://go.microsoft.com/fwlink/?LinkId=271946).</span></span>  
  
### <a name="next-lesson"></a><span data-ttu-id="b2ba3-137">次のレッスン</span><span class="sxs-lookup"><span data-stu-id="b2ba3-137">Next Lesson</span></span>  
 <span data-ttu-id="b2ba3-138">[レッスン 2: SQL Server 資格情報を作成する](../../2014/tutorials/lesson-2-create-a-sql-server-credential.md)。</span><span class="sxs-lookup"><span data-stu-id="b2ba3-138">[Lesson 2: Create a SQL Server Credential](../../2014/tutorials/lesson-2-create-a-sql-server-credential.md).</span></span>  
  
  
