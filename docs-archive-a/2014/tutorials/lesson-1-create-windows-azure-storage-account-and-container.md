---
title: 'レッスン 1: Azure Storage アカウントとコンテナーを作成する |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
ms.assetid: efdbd930-cde5-41b0-90ad-58a6cc68dddc
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 07167c513d2c6ed3ae0f7b431461ee3915047636
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632224"
---
# <a name="lesson-1-create-azure-storage-account-and-container"></a><span data-ttu-id="a69c2-102">レッスン 1:Azure Storage アカウントとコンテナーを作成する</span><span class="sxs-lookup"><span data-stu-id="a69c2-102">Lesson 1: Create Azure Storage Account and Container</span></span>
  <span data-ttu-id="a69c2-103">Azure Storage で SQL Server データファイルの格納を開始するには、まず Azure Storage アカウントと blob コンテナー、および shared access signature を作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a69c2-103">Before you can start storing SQL Server data files in Azure Storage, you must first create an Azure Storage account and a blob container, and a shared access signature.</span></span> <span data-ttu-id="a69c2-104">レッスン1では、Azure 管理ポータルにログインし、ストレージアカウント、blob コンテナー、および共有アクセス署名を作成する手順について説明します。</span><span class="sxs-lookup"><span data-stu-id="a69c2-104">Lesson 1 walks you through the steps of logging into the Azure Management Portal, creating a storage account, a blob container, and a shared access signature.</span></span>  
  
 <span data-ttu-id="a69c2-105">既定では、ストレージ アカウントの所有者だけがそのアカウント内の BLOB、テーブル、およびキューにアクセスすることができます。</span><span class="sxs-lookup"><span data-stu-id="a69c2-105">By default, only the owner of the storage account may access blobs, tables, and queues within that account.</span></span> <span data-ttu-id="a69c2-106">この新しい SQL Server の機能強化を使用して、ストレージ アカウント アクセス キーを共有しないで、これらのリソースにアクセスするには、次の操作をする必要があります。</span><span class="sxs-lookup"><span data-stu-id="a69c2-106">To be able to access these resources using this new SQL Server enhancement without sharing the storage account access key, you are required to do these:</span></span>  
  
-   <span data-ttu-id="a69c2-107">コンテナーの権限をプライベートに設定します。</span><span class="sxs-lookup"><span data-stu-id="a69c2-107">Set the container's permissions to private.</span></span>  
  
-   <span data-ttu-id="a69c2-108">Shared Access Signature を作成します。</span><span class="sxs-lookup"><span data-stu-id="a69c2-108">Create a shared access signature.</span></span> <span data-ttu-id="a69c2-109">これにより、リソースを利用可能な期間とクライアントに必要な権限を指定して、コンテナー、BLOB、テーブル、またはキュー リソースに対する制限付きアクセスをデリゲートすることができます。</span><span class="sxs-lookup"><span data-stu-id="a69c2-109">It enables you to delegate restricted access to a container, blob, table, or queue resource by specifying the interval for which the resources are available and the permissions that a client will have to it.</span></span>  
  
-   <span data-ttu-id="a69c2-110">保存されたアクセス ポリシーを使用して、コンテナーまたは BLOB の Shared Access Signature を管理します。</span><span class="sxs-lookup"><span data-stu-id="a69c2-110">Use a stored access policy to manage shared access signatures for a container or its blobs.</span></span> <span data-ttu-id="a69c2-111">保存されたアクセス ポリシーは、Shared Access Signatures をコントロールするもう 1 つの手段となり、それを取り消す直接的な手段にもなります。</span><span class="sxs-lookup"><span data-stu-id="a69c2-111">The stored access policy gives you an additional measure of control over your shared access signatures and also provides a straightforward means to revoke them.</span></span>  
  
 <span data-ttu-id="a69c2-112">詳細については、「 [Azure Storage リソースへのアクセスの管理](https://msdn.microsoft.com/library/windowsazure/ee393343.aspx)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a69c2-112">For more information, see [Manage Access to Azure Storage Resources](https://msdn.microsoft.com/library/windowsazure/ee393343.aspx).</span></span>  
  
## <a name="create-storage-account"></a><span data-ttu-id="a69c2-113">ストレージ アカウントの作成</span><span class="sxs-lookup"><span data-stu-id="a69c2-113">Create Storage Account</span></span>  
 <span data-ttu-id="a69c2-114">Azure 管理ポータルでストレージアカウントを作成するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="a69c2-114">To create a storage account on the Azure Management Portal, follow these steps:</span></span>  
  
1.  <span data-ttu-id="a69c2-115">アカウントを使用して[Azure 管理ポータル](https://manage.windowsazure.com)にログインします。</span><span class="sxs-lookup"><span data-stu-id="a69c2-115">Log in to the [Azure Management Portal](https://manage.windowsazure.com) using your account.</span></span> <span data-ttu-id="a69c2-116">Azure アカウントを持っていない場合は、 [Azure の無料試用版サイト](https://www.windowsazure.com/pricing/free-trial/)にアクセスしてください。</span><span class="sxs-lookup"><span data-stu-id="a69c2-116">If you do not have an Azure account, visit [Azure free trial](https://www.windowsazure.com/pricing/free-trial/).</span></span>  
  
     <span data-ttu-id="a69c2-117">![SQL 14 CTP2](../../2014/tutorials/media/ss-was-tutlesson-1-1.gif "SQL 14 CTP2")</span><span class="sxs-lookup"><span data-stu-id="a69c2-117">![SQL 14 CTP2](../../2014/tutorials/media/ss-was-tutlesson-1-1.gif "SQL 14 CTP2")</span></span>  
  
2.  <span data-ttu-id="a69c2-118">詳細な手順に従って、[ストレージアカウントを作成](https://azure.microsoft.com/documentation/articles/storage-create-storage-account/)します。</span><span class="sxs-lookup"><span data-stu-id="a69c2-118">Use the step by step instructions to [create a storage account](https://azure.microsoft.com/documentation/articles/storage-create-storage-account/).</span></span> <span data-ttu-id="a69c2-119">Azure 機能でのデータファイルの SQL Server に使用するストレージアカウントを作成する場合は、geo レプリケーションの選択を解除するか無効にする必要があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="a69c2-119">Note that when creating a storage account to be used for the SQL Server Data Files in Azure feature, you should unselect or disable the geo-replication.</span></span> <span data-ttu-id="a69c2-120">これは、地理的レプリケーションに参加している複数の BLOB では、書き込みの順序が保証されていないためです。</span><span class="sxs-lookup"><span data-stu-id="a69c2-120">This is because write order is not guaranteed for multiple blobs participating in geo-replication.</span></span> <span data-ttu-id="a69c2-121">ストレージ アカウントで地理的レプリケーションが実行されていて、復旧が必要になった場合、データが破損します。</span><span class="sxs-lookup"><span data-stu-id="a69c2-121">If a storage account is geo-replicated and recovery is required, a corruption occurs.</span></span>  
  
     <span data-ttu-id="a69c2-122">![SQL 14 CTP2](../../2014/tutorials/media/ss-was-tutlesson-1-2.gif "SQL 14 CTP2")</span><span class="sxs-lookup"><span data-stu-id="a69c2-122">![SQL 14 CTP2](../../2014/tutorials/media/ss-was-tutlesson-1-2.gif "SQL 14 CTP2")</span></span>  
  
## <a name="create-a-blob-container"></a><span data-ttu-id="a69c2-123">BLOB コンテナーを作成する</span><span class="sxs-lookup"><span data-stu-id="a69c2-123">Create a Blob container</span></span>  
 <span data-ttu-id="a69c2-124">Azure では、コンテナーは一連の blob をグループ化します。</span><span class="sxs-lookup"><span data-stu-id="a69c2-124">In Azure, a container provides a grouping of a set of blobs.</span></span> <span data-ttu-id="a69c2-125">すべての BLOB は 1 つのコンテナーに存在する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a69c2-125">All blobs must be in a container.</span></span> <span data-ttu-id="a69c2-126">ストレージ アカウントには、コンテナーを無制限に含めることができますが、少なくとも 1 つのコンテナーが必要です。</span><span class="sxs-lookup"><span data-stu-id="a69c2-126">A storage account can contain an unlimited number of containers, but must have at least one container.</span></span> <span data-ttu-id="a69c2-127">コンテナーには、BLOB を無制限に格納できます。</span><span class="sxs-lookup"><span data-stu-id="a69c2-127">A container can store an unlimited number of blobs.</span></span> <span data-ttu-id="a69c2-128">ストレージサイズの制限に関する最新情報については、「 [.net での Azure Blob Storage サービスの使用方法](https://www.windowsazure.com/develop/net/how-to-guides/blob-storage/)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a69c2-128">For most up-to-date information on storage size limits, see [How to use the Azure Blob Storage Service in .NET](https://www.windowsazure.com/develop/net/how-to-guides/blob-storage/).</span></span>  
  
 <span data-ttu-id="a69c2-129">Azure でコンテナーを作成するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="a69c2-129">To create a container in Azure, follow these steps:</span></span>  
  
1.  <span data-ttu-id="a69c2-130">[Azure 管理ポータル](https://manage.windowsazure.com)にログインします。</span><span class="sxs-lookup"><span data-stu-id="a69c2-130">Log in to the [Azure Management Portal](https://manage.windowsazure.com).</span></span>  
  
2.  <span data-ttu-id="a69c2-131">ストレージアカウントを選択し、[**コンテナー** ] タブをクリックし、画面の下部にある [**コンテナーの追加**] をクリックすると、新しいダイアログボックスが開きます。</span><span class="sxs-lookup"><span data-stu-id="a69c2-131">Select the storage account, click the **CONTAINERS** tab and click **ADD CONTAINER** at the bottom of the screen, which opens a new dialog box.</span></span>  
  
3.  <span data-ttu-id="a69c2-132">コンテナーの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="a69c2-132">Enter a name for the container.</span></span>  
  
4.  <span data-ttu-id="a69c2-133">[アクセスの**種類**] で [**プライベート**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="a69c2-133">Select **Private** for **Access Type**.</span></span> <span data-ttu-id="a69c2-134">アクセスをプライベートに設定すると、コンテナーと blob のデータは、Azure アカウントの所有者のみが読み取ることができます。</span><span class="sxs-lookup"><span data-stu-id="a69c2-134">When you set the access to private, the container and blob data can be read by the Azure account owner only.</span></span>  
  
     <span data-ttu-id="a69c2-135">![SQL 14 CTP2](../../2014/tutorials/media/ss-was-tutlesson-1-4.gif "SQL 14 CTP2")</span><span class="sxs-lookup"><span data-stu-id="a69c2-135">![SQL 14 CTP2](../../2014/tutorials/media/ss-was-tutlesson-1-4.gif "SQL 14 CTP2")</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a69c2-136">コンテナーをプログラムで作成するために、REST API を使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="a69c2-136">To create a container programmatically, you can also use REST APIs.</span></span> <span data-ttu-id="a69c2-137">詳細については、「 [Create Container](https://msdn.microsoft.com/library/windowsazure/dd179468.aspx) 」と「 [Azure Storage Services REST API リファレンス](https://msdn.microsoft.com/library/windowsazure/dd179355.aspx)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a69c2-137">For more information, see [Create Container](https://msdn.microsoft.com/library/windowsazure/dd179468.aspx) and also [Azure Storage Services REST API Reference](https://msdn.microsoft.com/library/windowsazure/dd179355.aspx).</span></span>  
  
 <span data-ttu-id="a69c2-138">**次のレッスン:**</span><span class="sxs-lookup"><span data-stu-id="a69c2-138">**Next Lesson:**</span></span>  
  
 [<span data-ttu-id="a69c2-139">レッスン2。コンテナーでポリシーを作成し、SAS&#41; キー &#40;Shared Access Signature を生成する</span><span class="sxs-lookup"><span data-stu-id="a69c2-139">Lesson 2. Create a policy on container and generate a Shared Access Signature &#40;SAS&#41; key</span></span>](../relational-databases/lesson-1-create-stored-access-policy-and-shared-access-signature.md)  
  
