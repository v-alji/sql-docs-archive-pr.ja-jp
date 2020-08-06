---
title: データベース オブジェクトへのアクセス権の付与 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- database access
ms.assetid: 686edfe2-3650-48a6-a2da-9d46fa211ad8
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 45b6d6c8dcd9c04d18489807271802aafee785b9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644742"
---
# <a name="granting-access-to-a-database"></a><span data-ttu-id="9ef70-102">データベースへのアクセス権の付与</span><span class="sxs-lookup"><span data-stu-id="9ef70-102">Granting Access to a Database</span></span>
  <span data-ttu-id="9ef70-103">これで Mary は [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]のこのインスタンスにアクセスできますが、データベースにアクセスする権限がありません。</span><span class="sxs-lookup"><span data-stu-id="9ef70-103">Mary now has access to this instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], but does not have permission to access the databases.</span></span> <span data-ttu-id="9ef70-104">データベースのユーザーとして承認されるまでは、既定の **TestData** データベースにさえアクセスできません。</span><span class="sxs-lookup"><span data-stu-id="9ef70-104">She does not even have access to her default database **TestData** until you authorize her as a database user.</span></span>  
  
 <span data-ttu-id="9ef70-105">Mary にアクセス権を与えるには、 **TestData** データベースに切り替えてから CREATE USER ステートメントを使用して、Mary という名のユーザーにそのログインをマップします。</span><span class="sxs-lookup"><span data-stu-id="9ef70-105">To grant Mary access, switch to the **TestData** database, and then use the CREATE USER statement to map her login to a user named Mary.</span></span>  
  
### <a name="to-create-a-user-in-a-database"></a><span data-ttu-id="9ef70-106">データベースにユーザーを作成するには</span><span class="sxs-lookup"><span data-stu-id="9ef70-106">To create a user in a database</span></span>  
  
1.  <span data-ttu-id="9ef70-107">次のステートメントを入力して実行し ( `computer_name` をコンピューターの名前に置き換える)、 `Mary` に `TestData` データベースへのアクセス権を与えます。</span><span class="sxs-lookup"><span data-stu-id="9ef70-107">Type and execute the following statements (replacing `computer_name` with the name of your computer) to grant `Mary` access to the `TestData` database.</span></span>  
  
    ```  
    USE [TestData];  
    GO  
  
    CREATE USER [Mary] FOR LOGIN [computer_name\Mary];  
    GO  
  
    ```  
  
     <span data-ttu-id="9ef70-108">これで、Mary は、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] と `TestData` の両方のデータベースにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="9ef70-108">Now, Mary has access to both [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] and the `TestData` database.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="9ef70-109">このレッスンの次の作業</span><span class="sxs-lookup"><span data-stu-id="9ef70-109">Next Task in Lesson</span></span>  
 [<span data-ttu-id="9ef70-110">ビューとストアドプロシージャの作成</span><span class="sxs-lookup"><span data-stu-id="9ef70-110">Creating Views and Stored Procedures</span></span>](lesson-2-3-creating-views-and-stored-procedures.md)  
  
  
