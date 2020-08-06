---
title: OPENROWSET 一括行セットプロバイダーを使用したラージオブジェクトデータの一括インポート (SQL Server) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-movement
ms.topic: conceptual
helpviewer_keywords:
- SINGLE_NCLOB option
- bulk rowset providers [SQL Server]
- bulk importing [SQL Server], data formats
- OPENROWSET function, bulk importing large data
- SINGLE_CLOB option
- data formats [SQL Server], large-object data
- large data, bulk imports
- SINGLE_BLOB option
ms.assetid: 171cdd5c-1e47-4bd7-b99a-4f0fd4e10526
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 0f43aa2fa5e7f7ef0b2c8f1f6e5e6ff28e02f9f1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639959"
---
# <a name="bulk-import-large-object-data-by-using-the-openrowset-bulk-rowset-provider-sql-server"></a><span data-ttu-id="e8eaf-102">OPENROWSET 一括行セット プロバイダーを使用したラージ オブジェクト データの一括インポート (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="e8eaf-102">Bulk Import Large-Object Data by using the OPENROWSET Bulk Rowset Provider (SQL Server)</span></span>
  <span data-ttu-id="e8eaf-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] OPENROWSET 一括行セット プロバイダーを使用すると、データ ファイルをラージ オブジェクト データとして一括インポートすることができます。</span><span class="sxs-lookup"><span data-stu-id="e8eaf-103">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] OPENROWSET Bulk Rowset Provider enables you to bulk import a data file as large-object data.</span></span>  
  
 <span data-ttu-id="e8eaf-104">OPENROWSET 一括行セット プロバイダーがサポートするラージ オブジェクト データ型は、 **varbinary**(max) (または **image**)、 **varchar**(max) (または **text**)、および **nvarchar**(max) (または **ntext**) です。</span><span class="sxs-lookup"><span data-stu-id="e8eaf-104">The large-object data types supported by OPENROWSET Bulk Rowset Provider are **varbinary**(max) or **image**, **varchar**(max) or **text**, and **nvarchar**(max) or **ntext**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e8eaf-105">**image**、 **text** 、 **ntext** の各データ型は非推奨とされます。</span><span class="sxs-lookup"><span data-stu-id="e8eaf-105">The **image**, **text** and **ntext** data types are deprecated.</span></span>  
  
 <span data-ttu-id="e8eaf-106">OPENROWSET BULK 句では、データ ファイルの内容を単一行、単一列の行セットとしてインポートするための 3 つのオプションがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="e8eaf-106">The OPENROWSET BULK clause supports three options for importing the contents of a data file as a single-row, single-column rowset.</span></span> <span data-ttu-id="e8eaf-107">フォーマット ファイルを使用する代わりに、ラージ オブジェクトのいずれかのオプションを指定できます。</span><span class="sxs-lookup"><span data-stu-id="e8eaf-107">You can specify one of these large-object options instead of using a format file.</span></span> <span data-ttu-id="e8eaf-108">これらのオプションを次に示します。</span><span class="sxs-lookup"><span data-stu-id="e8eaf-108">These options are as follows:</span></span>  
  
 <span data-ttu-id="e8eaf-109">SINGLE_BLOB</span><span class="sxs-lookup"><span data-stu-id="e8eaf-109">SINGLE_BLOB</span></span>  
 <span data-ttu-id="e8eaf-110">*data_file* の内容を単一行として読み取り、 **varbinary(max)** 型の単一列の行セットとして内容を返します。</span><span class="sxs-lookup"><span data-stu-id="e8eaf-110">Reads the contents of *data_file* as a single-row, returns the contents as a single-column rowset of type **varbinary(max)**.</span></span>  
  
 <span data-ttu-id="e8eaf-111">SINGLE_CLOB</span><span class="sxs-lookup"><span data-stu-id="e8eaf-111">SINGLE_CLOB</span></span>  
 <span data-ttu-id="e8eaf-112">指定したデータ ファイルの内容を文字として読み取り、テキストや **Word 文書などの現在のデータベースの照合順序を使用して、** varchar(max) [!INCLUDE[msCoName](../../includes/msconame-md.md)] 型の単一行および単一列の行セットとして内容を返します。</span><span class="sxs-lookup"><span data-stu-id="e8eaf-112">Reads the contents of the specified data file as characters, returns the contents as a single-row, single-column rowset of type **varchar(max)**, using the collation of the current database; such as a text or [!INCLUDE[msCoName](../../includes/msconame-md.md)] Word document.</span></span>  
  
 <span data-ttu-id="e8eaf-113">SINGLE_NCLOB</span><span class="sxs-lookup"><span data-stu-id="e8eaf-113">SINGLE_NCLOB</span></span>  
 <span data-ttu-id="e8eaf-114">指定したデータ ファイルの内容を Unicode として読み取り、現在のデータベースの照合順序を使用して、 **nvarchar(max)** 型の単一行および単一列の行セットとして内容を返します。</span><span class="sxs-lookup"><span data-stu-id="e8eaf-114">Reads the contents of the specified data file as Unicode, returns the contents as a single-row, single-column rowset of type **nvarchar(max)**, using the collation of the current database.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8eaf-115">参照</span><span class="sxs-lookup"><span data-stu-id="e8eaf-115">See Also</span></span>  
 <span data-ttu-id="e8eaf-116">[BULK INSERT または OPENROWSET&#40;BULK...&#41; を使用した一括データのインポート &#40;SQL Server&#41;](import-bulk-data-by-using-bulk-insert-or-openrowset-bulk-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="e8eaf-116">[Import Bulk Data by Using BULK INSERT or OPENROWSET&#40;BULK...&#41; &#40;SQL Server&#41;](import-bulk-data-by-using-bulk-insert-or-openrowset-bulk-sql-server.md) </span></span>  
 <span data-ttu-id="e8eaf-117">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="e8eaf-117">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span></span>  
 <span data-ttu-id="e8eaf-118">[OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="e8eaf-118">[OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql) </span></span>  
 <span data-ttu-id="e8eaf-119">[一括インポート中の NULL の保持または既定値の使用 &#40;SQL Server&#41;](keep-nulls-or-use-default-values-during-bulk-import-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="e8eaf-119">[Keep Nulls or Use Default Values During Bulk Import &#40;SQL Server&#41;](keep-nulls-or-use-default-values-during-bulk-import-sql-server.md) </span></span>  
 <span data-ttu-id="e8eaf-120">[bcp ユーティリティ](../../tools/bcp-utility.md) </span><span class="sxs-lookup"><span data-stu-id="e8eaf-120">[bcp Utility](../../tools/bcp-utility.md) </span></span>  
 [<span data-ttu-id="e8eaf-121">BULK INSERT &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="e8eaf-121">BULK INSERT &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/bulk-insert-transact-sql)  
  
  
