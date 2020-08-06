---
title: サーバーの照合順序の設定または変更 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- server collations [SQL Server]
- collations [SQL Server], server
ms.assetid: 3242deef-6f5f-4051-a121-36b3b4da851d
author: stevestein
ms.author: sstein
ms.openlocfilehash: 35e7be051c8cf63a272f2bf42fb54b1c45ed4160
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645655"
---
# <a name="set-or-change-the-server-collation"></a><span data-ttu-id="ec6a3-102">サーバーの照合順序の設定または変更</span><span class="sxs-lookup"><span data-stu-id="ec6a3-102">Set or Change the Server Collation</span></span>
  <span data-ttu-id="ec6a3-103">サーバー照合順序は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンスと一緒にインストールされているすべてのシステム データベースだけではなく、新しく作成したユーザー データベースの既定の照合順序になります。</span><span class="sxs-lookup"><span data-stu-id="ec6a3-103">The server collation acts as the default collation for all system databases that are installed with the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], and also any newly created user databases.</span></span> <span data-ttu-id="ec6a3-104">サーバー照合順序は [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインストール時に指定します。</span><span class="sxs-lookup"><span data-stu-id="ec6a3-104">The server collation is specified during [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installation.</span></span> <span data-ttu-id="ec6a3-105">詳細については、「 [Collation and Unicode Support](collation-and-unicode-support.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ec6a3-105">For more information, see [Collation and Unicode Support](collation-and-unicode-support.md).</span></span>  
  
## <a name="changing-the-server-collation"></a><span data-ttu-id="ec6a3-106">サーバー照合順序の変更</span><span class="sxs-lookup"><span data-stu-id="ec6a3-106">Changing the Server Collation</span></span>  
 <span data-ttu-id="ec6a3-107">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスの既定の照合順序を変更する操作は複雑で、次の手順が含まれます。</span><span class="sxs-lookup"><span data-stu-id="ec6a3-107">Changing the default collation for an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] can be a complex operation and involves the following steps:</span></span>  
  
-   <span data-ttu-id="ec6a3-108">ユーザー データベースおよびユーザー データベース内のすべてのオブジェクトを再作成するのに必要なすべての情報またはスクリプトがあることを確認します。</span><span class="sxs-lookup"><span data-stu-id="ec6a3-108">Make sure you have all the information or scripts needed to re-create your user databases and all the objects in them.</span></span>  
  
-   <span data-ttu-id="ec6a3-109">[bcp ユーティリティ](../../tools/bcp-utility.md)などのツールを使用して、すべてのデータをエクスポートします。</span><span class="sxs-lookup"><span data-stu-id="ec6a3-109">Export all your data using a tool such as the [bcp Utility](../../tools/bcp-utility.md).</span></span> <span data-ttu-id="ec6a3-110">詳細については、「[データの一括インポートと一括エクスポート &#40;SQL Server&#41;](../import-export/bulk-import-and-export-of-data-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ec6a3-110">For more information, see [Bulk Import and Export of Data &#40;SQL Server&#41;](../import-export/bulk-import-and-export-of-data-sql-server.md).</span></span>  
  
-   <span data-ttu-id="ec6a3-111">すべてのユーザー データベースを削除します。</span><span class="sxs-lookup"><span data-stu-id="ec6a3-111">Drop all the user databases.</span></span>  
  
-   <span data-ttu-id="ec6a3-112">**setup** コマンドの SQLCOLLATION プロパティで新しい照合順序を指定して、master データベースを再構築します。</span><span class="sxs-lookup"><span data-stu-id="ec6a3-112">Rebuild the master database specifying the new collation in the SQLCOLLATION property of the **setup** command.</span></span> <span data-ttu-id="ec6a3-113">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="ec6a3-113">For example:</span></span>  
  
    ```  
    Setup /QUIET /ACTION=REBUILDDATABASE /INSTANCENAME=InstanceName   
    /SQLSYSADMINACCOUNTS=accounts /[ SAPWD= StrongPassword ]   
    /SQLCOLLATION=CollationName  
    ```  
  
     <span data-ttu-id="ec6a3-114">詳細については、「 [システム データベースの再構築](../databases/system-databases.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ec6a3-114">For more information, see [Rebuild System Databases](../databases/system-databases.md).</span></span>  
  
-   <span data-ttu-id="ec6a3-115">すべてのデータベースとデータベース内のすべてのオブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="ec6a3-115">Create all the databases and all the objects in them.</span></span>  
  
-   <span data-ttu-id="ec6a3-116">すべてのデータをインポートします。</span><span class="sxs-lookup"><span data-stu-id="ec6a3-116">Import all your data.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ec6a3-117">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンスの既定の照合順序を変更する代わりに、新しく作成するデータベースごとに既定の照合順序を指定することができます。</span><span class="sxs-lookup"><span data-stu-id="ec6a3-117">Instead of changing the default collation of an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], you can specify a default collation for each new database you create.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec6a3-118">参照</span><span class="sxs-lookup"><span data-stu-id="ec6a3-118">See Also</span></span>  
 <span data-ttu-id="ec6a3-119">[照合順序と Unicode のサポート](collation-and-unicode-support.md) </span><span class="sxs-lookup"><span data-stu-id="ec6a3-119">[Collation and Unicode Support](collation-and-unicode-support.md) </span></span>  
 <span data-ttu-id="ec6a3-120">[データベースの照合順序の設定または変更](set-or-change-the-database-collation.md) </span><span class="sxs-lookup"><span data-stu-id="ec6a3-120">[Set or Change the Database Collation](set-or-change-the-database-collation.md) </span></span>  
 <span data-ttu-id="ec6a3-121">[列の照合順序の設定または変更](set-or-change-the-column-collation.md) </span><span class="sxs-lookup"><span data-stu-id="ec6a3-121">[Set or Change the Column Collation](set-or-change-the-column-collation.md) </span></span>  
 [<span data-ttu-id="ec6a3-122">システム データベースの再構築</span><span class="sxs-lookup"><span data-stu-id="ec6a3-122">Rebuild System Databases</span></span>](../databases/system-databases.md)  
  
  
