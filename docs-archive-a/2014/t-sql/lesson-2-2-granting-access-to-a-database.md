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
# <a name="granting-access-to-a-database"></a>データベースへのアクセス権の付与
  これで Mary は [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]のこのインスタンスにアクセスできますが、データベースにアクセスする権限がありません。 データベースのユーザーとして承認されるまでは、既定の **TestData** データベースにさえアクセスできません。  
  
 Mary にアクセス権を与えるには、 **TestData** データベースに切り替えてから CREATE USER ステートメントを使用して、Mary という名のユーザーにそのログインをマップします。  
  
### <a name="to-create-a-user-in-a-database"></a>データベースにユーザーを作成するには  
  
1.  次のステートメントを入力して実行し ( `computer_name` をコンピューターの名前に置き換える)、 `Mary` に `TestData` データベースへのアクセス権を与えます。  
  
    ```  
    USE [TestData];  
    GO  
  
    CREATE USER [Mary] FOR LOGIN [computer_name\Mary];  
    GO  
  
    ```  
  
     これで、Mary は、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] と `TestData` の両方のデータベースにアクセスできます。  
  
## <a name="next-task-in-lesson"></a>このレッスンの次の作業  
 [ビューとストアドプロシージャの作成](lesson-2-3-creating-views-and-stored-procedures.md)  
  
  
