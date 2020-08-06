---
title: 'レッスン 2: コンテナーでポリシーを作成し、Shared Access Signature (SAS) キーを生成する |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 41674d9d-8132-4bff-be4d-85a861419f3d
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: ab209f08d53b25a4791ef675e6fb6b78cab115f9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739930"
---
# <a name="lesson-2-create-a-policy-on-container-and-generate-a-shared-access-signature-sas-key"></a><span data-ttu-id="74cea-103">レッスン 2:</span><span class="sxs-lookup"><span data-stu-id="74cea-103">Lesson 2.</span></span> <span data-ttu-id="74cea-104">コンテナーのポリシーを作成し、Shared Access Signature (SAS) キーを生成する</span><span class="sxs-lookup"><span data-stu-id="74cea-104">Create a policy on container and generate a Shared Access Signature (SAS) key</span></span>
  <span data-ttu-id="74cea-105">このレッスンでは、BLOB コンテナーのポリシーを作成する方法と、SAS キーを生成する方法について学習します。</span><span class="sxs-lookup"><span data-stu-id="74cea-105">In this lesson, you will learn how to create a policy on the Blob container and also generate a SAS key.</span></span>  
  
 <span data-ttu-id="74cea-106">保存されたアクセス ポリシーによって、サーバー側の Shared Access Signature のコントロール レベルが 1 つ増えます。</span><span class="sxs-lookup"><span data-stu-id="74cea-106">A stored access policy provides an additional level of control over shared access signatures on the server side.</span></span> <span data-ttu-id="74cea-107">Shared Access Signature とは、コンテナー、BLOB、キュー、およびテーブルに対する制限付きアクセス権を付与する URI です。</span><span class="sxs-lookup"><span data-stu-id="74cea-107">A shared access signature is a URI that grants restricted access rights to containers, blobs, queues, and tables.</span></span> <span data-ttu-id="74cea-108">この新しい機能強化を使用する場合は、読み取り、書き込み、一覧表示の権限のあるコンテナーに対するポリシーを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="74cea-108">When using this new enhancement, you need to create a policy on a container with read, write, and list rights.</span></span>  
  
 <span data-ttu-id="74cea-109">次の方法の 1 つを使用してポリシーと Shared Access Signature を作成できます。</span><span class="sxs-lookup"><span data-stu-id="74cea-109">You can create a policy and a shared access signature by using one of the following methods:</span></span>  
  
-   <span data-ttu-id="74cea-110">Azure REST API 操作: コンテナーを[作成](https://msdn.microsoft.com/library/azure/dd179468.aspx)し、[コンテナー acl を設定](https://msdn.microsoft.com/library/azure/dd179391.aspx)して、[コンテナー acl を取得](https://msdn.microsoft.com/library/azure/dd179469.aspx)します。</span><span class="sxs-lookup"><span data-stu-id="74cea-110">Azure REST API operations: [Create Container](https://msdn.microsoft.com/library/azure/dd179468.aspx), [Set Container ACL](https://msdn.microsoft.com/library/azure/dd179391.aspx), and [Get Container ACL](https://msdn.microsoft.com/library/azure/dd179469.aspx).</span></span>  
  
-   <span data-ttu-id="74cea-111">Azure SDK の[CloudBlobContainer メソッド](https://docs.microsoft.com/dotnet/api/microsoft.azure.storage.blob.cloudblobcontainer.getsharedaccesssignature)を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="74cea-111">[CloudBlobContainer.GetSharedAccessSignature Method](https://docs.microsoft.com/dotnet/api/microsoft.azure.storage.blob.cloudblobcontainer.getsharedaccesssignature) in the Azure SDK.</span></span>  
  
    ```  
  
       string signature = blob.GetSharedAccessSignature(new SharedAccessPolicy()   
        {   
            // Specify the expiration time for the signature.   
            SharedAccessExpiryTime = DateTime.Now.Years(1),   
            // Specify the permissions granted by the signature.    
            Permissions = SharedAccessPermissions.Write | SharedAccessPermissions.Read   
        });  
  
    ```  
  
-   <span data-ttu-id="74cea-112">[Azure Storage Explorer](https://azurestorageexplorer.codeplex.com/)などのサードパーティの Azure explorer ツール。</span><span class="sxs-lookup"><span data-stu-id="74cea-112">A third-party Azure explorer tool, such as [Azure Storage Explorer](https://azurestorageexplorer.codeplex.com/).</span></span>  
  
 <span data-ttu-id="74cea-113">**次のレッスン:**</span><span class="sxs-lookup"><span data-stu-id="74cea-113">**Next Lesson:**</span></span>  
  
 [<span data-ttu-id="74cea-114">レッスン 3:SQL Server 資格情報の作成</span><span class="sxs-lookup"><span data-stu-id="74cea-114">Lesson 3: Create a SQL Server Credential</span></span>](../relational-databases/lesson-2-create-a-sql-server-credential-using-a-shared-access-signature.md)  
  
