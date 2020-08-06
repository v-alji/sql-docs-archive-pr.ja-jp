---
title: Oracle テーブルスペースの管理 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- Oracle publishing [SQL Server replication], managing tablespaces
- tablespaces [SQL Server replication]
ms.assetid: b8ea6c3b-01d6-4efc-bbfb-03b264530bbd
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: a3624aed38a7a5bf75e0c0807aa8d3657156264f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87717924"
---
# <a name="manage-oracle-tablespaces"></a><span data-ttu-id="c0c6f-102">Oracle テーブルスペースの管理</span><span class="sxs-lookup"><span data-stu-id="c0c6f-102">Manage Oracle Tablespaces</span></span>
  <span data-ttu-id="c0c6f-103">テーブルスペースは、[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のファイル グループにほぼ等しいデータベース領域の単位です。</span><span class="sxs-lookup"><span data-stu-id="c0c6f-103">A tablespace is a unit of database storage that is roughly equivalent to a file group in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="c0c6f-104">テーブルスペースでは、個々のグループ内でデータベース オブジェクトの格納および管理が可能です。</span><span class="sxs-lookup"><span data-stu-id="c0c6f-104">Tablespaces allow storage and management of database objects within individual groups.</span></span> <span data-ttu-id="c0c6f-105">詳細については Oracle のマニュアルを参照してください。</span><span class="sxs-lookup"><span data-stu-id="c0c6f-105">For more information, see the Oracle documentation.</span></span>  
  
 <span data-ttu-id="c0c6f-106">Oracle パブリケーションの一部としてテーブルを構成する場合、必要に応じて、レプリケーション ログ情報を格納するときに既存の Oracle テーブルスペースを使用するように指定できます。</span><span class="sxs-lookup"><span data-stu-id="c0c6f-106">When you configure a table as part of an Oracle publication, you can optionally specify an existing Oracle tablespace to be used when storing replication logging information.</span></span> <span data-ttu-id="c0c6f-107">指定しない場合、レプリケーション オブジェクトのテーブルスペースは、パブリッシャーの構成時に構成したレプリケーション管理ユーザー スキーマに関連付けられた既定のテーブルスペースとなります。</span><span class="sxs-lookup"><span data-stu-id="c0c6f-107">If unspecified, the tablespace for the replication objects is the default tablespace associated with the replication administrative user schema that was configured when configuring the Publisher.</span></span>  
  
 <span data-ttu-id="c0c6f-108">**アーティクルのログ テーブルのテーブルスペースを指定するには**</span><span class="sxs-lookup"><span data-stu-id="c0c6f-108">**To specify a tablespace for an article logging table**:</span></span>  
  
-   <span data-ttu-id="c0c6f-109">**[アーティクルのプロパティ]** ダイアログ ボックスでテーブルスペースを指定します。</span><span class="sxs-lookup"><span data-stu-id="c0c6f-109">Specify a tablespace in the **Article Properties** dialog box.</span></span> <span data-ttu-id="c0c6f-110">このダイアログ ボックスへのアクセス方法の詳細については、「[パブリケーション プロパティの表示および変更](../publish/view-and-modify-publication-properties.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c0c6f-110">For more information about accessing this dialog box, see [View and Modify Publication Properties](../publish/view-and-modify-publication-properties.md).</span></span>  
  
-   <span data-ttu-id="c0c6f-111">[sp_changearticle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-changearticle-transact-sql) を使用します。</span><span class="sxs-lookup"><span data-stu-id="c0c6f-111">Use [sp_changearticle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-changearticle-transact-sql).</span></span> <span data-ttu-id="c0c6f-112">**sp_changearticle**を使用するには、以下を指定します。</span><span class="sxs-lookup"><span data-stu-id="c0c6f-112">To use **sp_changearticle**, specify the following:</span></span>  
  
    -   <span data-ttu-id="c0c6f-113">パラメーターに対して Oracle パブリッシャーの名前を指定 **@publisher** します。</span><span class="sxs-lookup"><span data-stu-id="c0c6f-113">The name of the Oracle Publisher for the parameter **@publisher**.</span></span>  
  
    -   <span data-ttu-id="c0c6f-114">パラメーターに対して Oracle パブリケーションの名前を指定し **@publication** ます。</span><span class="sxs-lookup"><span data-stu-id="c0c6f-114">The name of the Oracle publication for the parameter **@publication**.</span></span>  
  
    -   <span data-ttu-id="c0c6f-115">パラメーターのアーティクルの名前 **@article** です。</span><span class="sxs-lookup"><span data-stu-id="c0c6f-115">The name of the article for the parameter **@article**.</span></span>  
  
    -   <span data-ttu-id="c0c6f-116">パラメーターの値 ' テーブルスペース ' **@property** 。</span><span class="sxs-lookup"><span data-stu-id="c0c6f-116">A value of 'tablespace' for the parameter **@property**.</span></span>  
  
    -   <span data-ttu-id="c0c6f-117">パラメーターのテーブルスペースの名前 **@value** 。</span><span class="sxs-lookup"><span data-stu-id="c0c6f-117">The name of the tablespace for the parameter **@value**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0c6f-118">参照</span><span class="sxs-lookup"><span data-stu-id="c0c6f-118">See Also</span></span>  
 <span data-ttu-id="c0c6f-119">[Configure an Oracle Publisher (Oracle パブリッシャーの構成)](configure-an-oracle-publisher.md) </span><span class="sxs-lookup"><span data-stu-id="c0c6f-119">[Configure an Oracle Publisher](configure-an-oracle-publisher.md) </span></span>  
 [<span data-ttu-id="c0c6f-120">Oracle パブリッシャー上で作成されたオブジェクト</span><span class="sxs-lookup"><span data-stu-id="c0c6f-120">Objects Created on the Oracle Publisher</span></span>](objects-created-on-the-oracle-publisher.md)  
  
  
