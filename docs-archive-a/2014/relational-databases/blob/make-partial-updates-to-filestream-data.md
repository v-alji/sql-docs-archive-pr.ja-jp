---
title: FILESTREAM データの部分的な更新 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: filestream
ms.topic: conceptual
helpviewer_keywords:
- FILESTREAM [SQL Server], FSCTL_SQL_FILESTREAM_FETCH_OLD_CONTENT
- FSCTL_SQL_FILESTREAM_FETCH_OLD_CONTENT
ms.assetid: d6f7661e-6c14-4d31-9541-4520ca0f82b2
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 696c1a6421e14568877e24f015e5094395f1051b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740033"
---
# <a name="make-partial-updates-to-filestream-data"></a><span data-ttu-id="60989-102">FILESTREAM データの部分的な更新</span><span class="sxs-lookup"><span data-stu-id="60989-102">Make Partial Updates to FILESTREAM Data</span></span>
  <span data-ttu-id="60989-103">アプリケーションでは、FSCTL_SQL_FILESTREAM_FETCH_OLD_CONTENT を使用して FILESTREAM BLOB データを部分的に更新します。</span><span class="sxs-lookup"><span data-stu-id="60989-103">An application uses FSCTL_SQL_FILESTREAM_FETCH_OLD_CONTENT to make partial updates to FILESTREAM BLOB data.</span></span> <span data-ttu-id="60989-104">[DeviceIoControl](https://go.microsoft.com/fwlink/?LinkId=105527) 関数は、この値と、 [OpenSqlFilestream](access-filestream-data-with-opensqlfilestream.md) から FILESTREAM ドライバーに返されるハンドルを渡します。</span><span class="sxs-lookup"><span data-stu-id="60989-104">The [DeviceIoControl](https://go.microsoft.com/fwlink/?LinkId=105527) function passes this value and the handle that is returned from [OpenSqlFilestream](access-filestream-data-with-opensqlfilestream.md) to the FILESTREAM driver.</span></span> <span data-ttu-id="60989-105">このドライバーによって、サーバー側の現在の FILESTREAM データが、ハンドルが参照するファイルにコピーされます。</span><span class="sxs-lookup"><span data-stu-id="60989-105">The driver then forces a server-side copy of the current FILESTREAM data into the file that is referenced by the handle.</span></span> <span data-ttu-id="60989-106">ハンドルへの書き込みが行われた後にアプリケーションが FSCTL_SQL_FILESTREAM_FETCH_OLD_CONTENT 値を発行すると、最後の書き込み操作は維持され、それより前のハンドルへの書き込み操作は失われます。</span><span class="sxs-lookup"><span data-stu-id="60989-106">If the application issues the FSCTL_SQL_FILESTREAM_FETCH_OLD_CONTENT value after the handle has been written to, the last write operation persists and previous write operations that were made to the handle are lost.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="60989-107">FILESTREAM のリモート アクセスは、 [SMB プロトコル](https://go.microsoft.com/fwlink/?LinkId=112454) に依存しています。</span><span class="sxs-lookup"><span data-stu-id="60989-107">FILESTREAM relies on the [SMB protocol](https://go.microsoft.com/fwlink/?LinkId=112454) for remote access.</span></span>  
  
## <a name="example"></a><span data-ttu-id="60989-108">例</span><span class="sxs-lookup"><span data-stu-id="60989-108">Example</span></span>  
 <span data-ttu-id="60989-109">次の例では、 `FSCTL_SQL_FILESTREAM_FETCH_OLD_CONTENT` 値を使用して、挿入された FILESTREAM BLOB を部分的に更新する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="60989-109">The following example shows you how to use the `FSCTL_SQL_FILESTREAM_FETCH_OLD_CONTENT` value to perform a partial update of an inserted FILESTREAM BLOB.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="60989-110">この例では、「 [FILESTREAM が有効なデータベースを作成する方法](create-a-filestream-enabled-database.md) 」および「 [FILESTREAM データを格納するテーブルを作成する方法](create-a-table-for-storing-filestream-data.md)」で作成した、FILESTREAM が有効なデータベースとテーブルが必要です。</span><span class="sxs-lookup"><span data-stu-id="60989-110">This example requires the FILESTREAM-enabled database and table that are created in [Create a FILESTREAM-Enabled Database](create-a-filestream-enabled-database.md) and [Create a Table for Storing FILESTREAM Data](create-a-table-for-storing-filestream-data.md).</span></span>  
  
 [!code-cpp[FILESTREAM#FS_CPP_FSCTL](../../snippets/tsql/SQL15/tsql/filestream/cpp/filestream.cpp#fs_cpp_fsctl)]  
  
## <a name="see-also"></a><span data-ttu-id="60989-111">参照</span><span class="sxs-lookup"><span data-stu-id="60989-111">See Also</span></span>  
 <span data-ttu-id="60989-112">[OpenSqlFilestream による FILESTREAM データへのアクセス](access-filestream-data-with-opensqlfilestream.md) </span><span class="sxs-lookup"><span data-stu-id="60989-112">[Access FILESTREAM Data with OpenSqlFilestream](access-filestream-data-with-opensqlfilestream.md) </span></span>  
 [<span data-ttu-id="60989-113">FILESTREAM データ用のクライアント アプリケーションの作成</span><span class="sxs-lookup"><span data-stu-id="60989-113">Create Client Applications for FILESTREAM Data</span></span>](create-client-applications-for-filestream-data.md)  
  
  
