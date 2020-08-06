---
title: Oracle への接続 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- connOra
ms.assetid: 711ac7ff-5d3d-4533-80ca-d1fecdb3048f
author: chugugrace
ms.author: chugu
ms.openlocfilehash: e6546e3bbde666107ed7757c41d98d5b7b598924
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738640"
---
# <a name="connect-to-oracle"></a><span data-ttu-id="1e517-102">Oracle への接続</span><span class="sxs-lookup"><span data-stu-id="1e517-102">Connect to Oracle</span></span>
  <span data-ttu-id="1e517-103">CDC インスタンスに使用するテーブルを初めて追加または編集するとき、Oracle データベースへの接続を要求されることがあります。</span><span class="sxs-lookup"><span data-stu-id="1e517-103">When you add or edit the tables used in the CDC instance for the first time, you may be asked to connect to the Oracle database.</span></span> <span data-ttu-id="1e517-104">キャプチャするテーブルのスキーマにアクセスできる Oracle ユーザーの資格情報を入力する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1e517-104">You should enter the credentials of an Oracle user who can access the schema of the tables to be captured.</span></span> <span data-ttu-id="1e517-105">このダイアログ ボックスでは次の情報を入力します。</span><span class="sxs-lookup"><span data-stu-id="1e517-105">Enter the following in this dialog box:</span></span>  
  
 <span data-ttu-id="1e517-106">**認証**</span><span class="sxs-lookup"><span data-stu-id="1e517-106">**Authentication**</span></span>  
  
 <span data-ttu-id="1e517-107">次のいずれかを選択してください。</span><span class="sxs-lookup"><span data-stu-id="1e517-107">Select one of the following:</span></span>  
  
-   <span data-ttu-id="1e517-108">**[Windows 認証]** : 現在の Windows ドメイン資格情報を使用する場合に選択します。</span><span class="sxs-lookup"><span data-stu-id="1e517-108">**Windows Authentication**: Select this to use the current Windows domain credentials.</span></span> <span data-ttu-id="1e517-109">このオプションは、Oracle データベースが Windows 認証と連動するように構成されている場合にのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="1e517-109">You can use this option only if the Oracle database is configured to work with Windows authentication.</span></span>  
  
-   <span data-ttu-id="1e517-110">**[Oracle 認証]** : このオプションを選択する場合、接続先の Oracle データベースのユーザーの **[ユーザー名]** と **[パスワード]** を入力する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1e517-110">**Oracle Authentication**: If you select this option, you must type the **User Name** and **Password** for the user in the Oracle database you are connecting to.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e517-111">参照</span><span class="sxs-lookup"><span data-stu-id="1e517-111">See Also</span></span>  
 [<span data-ttu-id="1e517-112">CDC へのテーブルの追加</span><span class="sxs-lookup"><span data-stu-id="1e517-112">Add Tables to a CDC Instance</span></span>](add-tables-to-a-cdc-instance.md)  
  
  
