---
title: 'レッスン 2: データベース オブジェクトに対するアクセス許可の構成 | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: t-sql
ms.topic: conceptual
helpviewer_keywords:
- database permissions
ms.assetid: f964b66a-ec32-44c2-a185-6a0f173bfa22
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: fcc6ee3ddf9be072b51bd568fd3e72eb6c871785
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740653"
---
# <a name="lesson-2-configuring-permissions-on-database-objects"></a><span data-ttu-id="2e9cb-102">レッスン 2: データベース オブジェクトに対する権限の構成</span><span class="sxs-lookup"><span data-stu-id="2e9cb-102">Lesson 2: Configuring Permissions on Database Objects</span></span>
  <span data-ttu-id="2e9cb-103">データベースへのアクセス権をユーザーに付与するには、次の 3 つの手順があります。</span><span class="sxs-lookup"><span data-stu-id="2e9cb-103">Granting a user access to a database involves three steps.</span></span> <span data-ttu-id="2e9cb-104">まず、ログインを作成します。</span><span class="sxs-lookup"><span data-stu-id="2e9cb-104">First, you create a login.</span></span> <span data-ttu-id="2e9cb-105">ユーザーはこのログインを使用して、 [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)]に接続できます。</span><span class="sxs-lookup"><span data-stu-id="2e9cb-105">The login lets the user connect to the [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)].</span></span> <span data-ttu-id="2e9cb-106">次に、指定したデータベースでユーザーとしてログインを構成します。</span><span class="sxs-lookup"><span data-stu-id="2e9cb-106">Then you configure the login as a user in the specified database.</span></span> <span data-ttu-id="2e9cb-107">最後に、データベース オブジェクトに対する権限をユーザーに付与します。</span><span class="sxs-lookup"><span data-stu-id="2e9cb-107">And finally, you grant that user permission to database objects.</span></span> <span data-ttu-id="2e9cb-108">このレッスンではこれらの 3 つの手順を紹介し、ビューとストアド プロシージャをオブジェクトとして作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="2e9cb-108">This lesson shows you these three steps, and shows you how to create a view and a stored procedure as the object.</span></span>  
  
 <span data-ttu-id="2e9cb-109">このレッスンの内容は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="2e9cb-109">This lesson contains the following topics:</span></span>  
  
-   [<span data-ttu-id="2e9cb-110">ログインの作成</span><span class="sxs-lookup"><span data-stu-id="2e9cb-110">Creating a Login</span></span>](lesson-2-1-creating-a-login.md)  
  
-   [<span data-ttu-id="2e9cb-111">データベースへのアクセス権の付与</span><span class="sxs-lookup"><span data-stu-id="2e9cb-111">Granting Access to a Database</span></span>](lesson-2-2-granting-access-to-a-database.md)  
  
-   [<span data-ttu-id="2e9cb-112">ビューとストアドプロシージャの作成</span><span class="sxs-lookup"><span data-stu-id="2e9cb-112">Creating Views and Stored Procedures</span></span>](lesson-2-3-creating-views-and-stored-procedures.md)  
  
-   [<span data-ttu-id="2e9cb-113">データベース オブジェクトへのアクセス権の付与</span><span class="sxs-lookup"><span data-stu-id="2e9cb-113">Granting Access to a Database Object</span></span>](lesson-2-4-granting-access-to-a-database-object.md)  
  
-   [<span data-ttu-id="2e9cb-114">概要 : データベース オブジェクトに対する権限の構成</span><span class="sxs-lookup"><span data-stu-id="2e9cb-114">Summary: Configuring Permissions on Database Objects</span></span>](lesson-2-5-summary-configuring-permissions-on-database-objects.md)  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="2e9cb-115">このレッスンの次の作業</span><span class="sxs-lookup"><span data-stu-id="2e9cb-115">Next Task in Lesson</span></span>  
 [<span data-ttu-id="2e9cb-116">ログインの作成</span><span class="sxs-lookup"><span data-stu-id="2e9cb-116">Creating a Login</span></span>](lesson-2-1-creating-a-login.md)  
  
  
