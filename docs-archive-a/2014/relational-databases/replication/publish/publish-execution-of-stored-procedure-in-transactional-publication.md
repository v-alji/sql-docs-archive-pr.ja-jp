---
title: トランザクションパブリケーションでのストアドプロシージャの実行のパブリッシュ (SQL Server Management Studio) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- publishing [SQL Server replication], stored procedure execution
- stored procedures [SQL Server replication], publishing
ms.assetid: 1d3a3525-0bc5-466f-b097-5359dc74432d
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 44310d45a7049701a6aecfa73301b15b0021ac6f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633059"
---
# <a name="publish-the-execution-of-a-stored-procedure-in-a-transactional-publication-sql-server-management-studio"></a><span data-ttu-id="7db75-102">トランザクション パブリケーションでのストアド プロシージャの実行のパブリッシュ (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="7db75-102">Publish the Execution of a Stored Procedure in a Transactional Publication (SQL Server Management Studio)</span></span>
  <span data-ttu-id="7db75-103">**[アーティクルのプロパティ - \<Article>]** ダイアログ ボックスで、ストアド プロシージャの単なる定義ではなく、その実行をパブリッシュすることを指定します。</span><span class="sxs-lookup"><span data-stu-id="7db75-103">Specify that the execution of a stored procedure (rather than just its definition) should be published in the **Article Properties - \<Article>** dialog box.</span></span> <span data-ttu-id="7db75-104">このダイアログ ボックスは、パブリケーションの新規作成ウィザードおよび **[パブリケーションのプロパティ - \<Publication>]** ダイアログ ボックスで使用できます。</span><span class="sxs-lookup"><span data-stu-id="7db75-104">This dialog box is available in the New Publication Wizard and the **Publication Properties - \<Publication>** dialog box.</span></span> <span data-ttu-id="7db75-105">ウィザードの使用およびダイアログ ボックスへのアクセスの詳細については、「[パブリケーションの作成](create-a-publication.md)」および「[View and Modify Publication Properties](view-and-modify-publication-properties.md)」 (パブリケーション プロパティの表示および変更) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7db75-105">For more information about using the wizard and accessing the dialog box, see [Create a Publication](create-a-publication.md) and [View and Modify Publication Properties](view-and-modify-publication-properties.md).</span></span>  
  
 <span data-ttu-id="7db75-106">プロシージャの定義 (CREATE PROCEDURE ステートメント) はサブスクリプションが初期化されるときにサブスクライバーにレプリケートされます。プロシージャがパブリッシャーで実行されるときに、レプリケーションは対応するプロシージャをサブスクライバーで実行します。</span><span class="sxs-lookup"><span data-stu-id="7db75-106">The definition of the procedure (the CREATE PROCEDURE statement) is replicated to the Subscriber when the subscription is initialized; when the procedure is executed at the Publisher, replication executes the corresponding procedure at the Subscriber.</span></span>  
  
### <a name="to-publish-the-execution-of-a-stored-procedure"></a><span data-ttu-id="7db75-107">ストアド プロシージャの実行をパブリッシュするには</span><span class="sxs-lookup"><span data-stu-id="7db75-107">To publish the execution of a stored procedure</span></span>  
  
1.  <span data-ttu-id="7db75-108">パブリケーションの新規作成ウィザードまたは **[パブリケーションのプロパティ - \<Publication>]** ダイアログ ボックスの **[アーティクル]** ページで、ストアド プロシージャを選択します。</span><span class="sxs-lookup"><span data-stu-id="7db75-108">On the **Articles** page of the New Publication Wizard or the **Publication Properties - \<Publication>** dialog box, select a stored procedure.</span></span>  
  
2.  <span data-ttu-id="7db75-109">**[アーティクルのプロパティ]** をクリックしてから、 **[反転表示されたストアド プロシージャのプロパティを設定]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7db75-109">Click **Article Properties**, and then click **Set Properties of Highlighted Stored Procedure**.</span></span>  
  
3.  <span data-ttu-id="7db75-110">**[アーティクルのプロパティ - \<Article>]** ダイアログ ボックスで、 **[レプリケート]** オプションに対して次のいずれかの値を指定します。</span><span class="sxs-lookup"><span data-stu-id="7db75-110">In the **Article Properties - \<Article>** dialog box, specify one of the following values for the **Replicate** option:</span></span>  
  
    -   <span data-ttu-id="7db75-111">**[ストアド プロシージャの実行]**</span><span class="sxs-lookup"><span data-stu-id="7db75-111">**Execution of the stored procedure**</span></span>  
  
    -   <span data-ttu-id="7db75-112">**[SP のシリアル化されたトランザクションでの実行]**</span><span class="sxs-lookup"><span data-stu-id="7db75-112">**Execution in a serialized transaction of the SP**</span></span>  
  
         <span data-ttu-id="7db75-113">これは、推奨オプションです。このオプションを指定すると、プロシージャがシリアル化可能なトランザクションのコンテキスト内で実行される場合にのみ、プロシージャの実行がレプリケートされます。</span><span class="sxs-lookup"><span data-stu-id="7db75-113">This is the recommended option, because it replicates the procedure execution only if the procedure is executed within the context of a serializable transaction.</span></span> <span data-ttu-id="7db75-114">ストアド プロシージャがシリアル化可能なトランザクションの外から実行される場合、パブリッシュされたテーブルのデータに対する変更は一連の DML (データ操作言語) ステートメントとしてレプリケートされます。</span><span class="sxs-lookup"><span data-stu-id="7db75-114">If the stored procedure is executed outside of a serializable transaction, changes to data in published tables are replicated as a series of data manipulation language (DML) statements.</span></span>  
  
4.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
5.  <span data-ttu-id="7db75-115">**[パブリケーションのプロパティ - \<Publication>]** ダイアログ ボックスが表示されている場合は、 **[OK]** をクリックして保存し、ダイアログ ボックスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="7db75-115">If you are in the **Publication Properties - \<Publication>** dialog box, click **OK** to save and close the dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7db75-116">参照</span><span class="sxs-lookup"><span data-stu-id="7db75-116">See Also</span></span>  
 [<span data-ttu-id="7db75-117">トランザクション レプリケーションにおけるパブリッシング ストアド プロシージャの実行</span><span class="sxs-lookup"><span data-stu-id="7db75-117">Publishing Stored Procedure Execution in Transactional Replication</span></span>](../transactional/publishing-stored-procedure-execution-in-transactional-replication.md)  
  
  
