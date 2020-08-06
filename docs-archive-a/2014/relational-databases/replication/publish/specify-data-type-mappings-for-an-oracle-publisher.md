---
title: Oracle パブリッシャーのデータ型マッピングの指定 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- Oracle publishing [SQL Server replication], data type mapping
- data types [SQL Server replication], Oracle publishing
- mapping data types [SQL Server replication]
ms.assetid: f172d631-3b8c-4912-bd0f-568366cd9870
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 26331e3864940b9c7f2a2588e3d3cbfa9944c900
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87721290"
---
# <a name="specify-data-type-mappings-for-an-oracle-publisher"></a><span data-ttu-id="cd27b-102">Oracle パブリッシャーのデータ型マッピングの指定</span><span class="sxs-lookup"><span data-stu-id="cd27b-102">Specify Data Type Mappings for an Oracle Publisher</span></span>
  <span data-ttu-id="cd27b-103">このトピックでは、 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] で [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[tsql](../../../includes/tsql-md.md)]を使用して、Oracle パブリッシャーのデータ型マッピングを指定する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="cd27b-103">This topic describes how to specify data type mappings for an Oracle Publisher in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../../includes/tsql-md.md)].</span></span> <span data-ttu-id="cd27b-104">Oracle パブリッシャーには一連の既定のデータ型マッピングが用意されていますが、パブリケーションによっては、こうした既定のマッピングとは異なるマッピングの指定が必要になる場合もあります。</span><span class="sxs-lookup"><span data-stu-id="cd27b-104">Although a set of default data type mappings are provided for Oracle Publishers, it might be necessary to specify different mappings for a given publication.</span></span>  
  
 <span data-ttu-id="cd27b-105">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="cd27b-105">**In This Topic**</span></span>  
  
-   <span data-ttu-id="cd27b-106">**Oracle パブリッシャーのデータ型マッピングを指定するために使用するもの:**</span><span class="sxs-lookup"><span data-stu-id="cd27b-106">**To specify data type mappings for an Oracle Publisher, using:**</span></span>  
  
     [<span data-ttu-id="cd27b-107">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="cd27b-107">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="cd27b-108">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="cd27b-108">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="cd27b-109">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="cd27b-109">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="cd27b-110">データ型マッピングは、 **[アーティクルのプロパティ - \<Article>]** ダイアログ ボックスの **[データのマッピング]** タブで指定します。</span><span class="sxs-lookup"><span data-stu-id="cd27b-110">Specify data type mappings on the **Data Mapping** tab of the **Article Properties - \<Article>** dialog box.</span></span> <span data-ttu-id="cd27b-111">このタブは、パブリケーションの新規作成ウィザードの **[アーティクル]** ページおよび **[パブリケーションのプロパティ - \<Publication>]** ダイアログ ボックスから利用できます。</span><span class="sxs-lookup"><span data-stu-id="cd27b-111">This is available from the **Articles** page of the New Publication Wizard and the **Publication Properties - \<Publication>** dialog box.</span></span> <span data-ttu-id="cd27b-112">ウィザードの使用およびダイアログ ボックスへのアクセスの詳細については、「[Oracle データベースからのパブリケーションの作成](create-a-publication-from-an-oracle-database.md)」および「[パブリケーション プロパティの表示および変更](view-and-modify-publication-properties.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cd27b-112">For more information about using the wizard and accessing the dialog box, see [Create a Publication from an Oracle Database](create-a-publication-from-an-oracle-database.md) and [View and Modify Publication Properties](view-and-modify-publication-properties.md).</span></span>  
  
#### <a name="to-specify-a-data-type-mapping"></a><span data-ttu-id="cd27b-113">データ型マッピングを指定するには</span><span class="sxs-lookup"><span data-stu-id="cd27b-113">To specify a data type mapping</span></span>  
  
1.  <span data-ttu-id="cd27b-114">パブリケーションの新規作成ウィザードの **[アーティクル]** ページ、または **[パブリケーションのプロパティ - \<Publication>]** ダイアログ ボックスでテーブルを選択し、 **[アーティクルのプロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="cd27b-114">On the **Articles** page of the New Publication Wizard or the **Publication Properties - \<Publication>** dialog box, select a table, and then click **Article Properties**.</span></span>  
  
2.  <span data-ttu-id="cd27b-115">**[反転表示されたテーブル アーティクルのプロパティを設定]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="cd27b-115">Click **Set Properties of Highlighted Table Article**.</span></span>  
  
3.  <span data-ttu-id="cd27b-116">**[アーティクルのプロパティ - \<Article>]** ダイアログ ボックスの **[データのマッピング]** タブで、 **[サブスクライバーのデータ型]** 列からマッピングを選択します。</span><span class="sxs-lookup"><span data-stu-id="cd27b-116">On the **Data Mapping** tab of the **Article Properties - \<Article>** dialog box, select mappings from the **Subscriber Data Type** column:</span></span>  
  
    -   <span data-ttu-id="cd27b-117">データ型によっては、可能なマッピングが 1 つしかない場合があります。このような場合、プロパティ グリッドの列は読み取り専用になります。</span><span class="sxs-lookup"><span data-stu-id="cd27b-117">For some data types there is only one possible mapping, in which case the column in the property grid is read-only.</span></span>  
  
    -   <span data-ttu-id="cd27b-118">データ型によっては、複数のデータ型を選択できる場合があります。</span><span class="sxs-lookup"><span data-stu-id="cd27b-118">For some types, there is more than one type that you can select.</span></span> [!INCLUDE[msCoName](../../../includes/msconame-md.md)] <span data-ttu-id="cd27b-119">では、アプリケーションに別のマッピングが必要でない限り、既定のマッピングを使うことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="cd27b-119">recommends that you use the default mapping unless your application requires a different mapping.</span></span> <span data-ttu-id="cd27b-120">詳しくは、「 [Data Type Mapping for Oracle Publishers](../non-sql/data-type-mapping-for-oracle-publishers.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="cd27b-120">For more information, see [Data Type Mapping for Oracle Publishers](../non-sql/data-type-mapping-for-oracle-publishers.md).</span></span>  
  
4.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="cd27b-121">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="cd27b-121">Using Transact-SQL</span></span>  
 <span data-ttu-id="cd27b-122">レプリケーションのストアド プロシージャを使用すると、カスタム データ型マッピングをプログラムから指定できます。</span><span class="sxs-lookup"><span data-stu-id="cd27b-122">You can specify custom data type mappings programmatically using replication stored procedures.</span></span> <span data-ttu-id="cd27b-123">[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] と以外の [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] データベース管理システム (DBMS) の間でデータ型をマップするときに使用される既定のマッピングを設定することもできます。</span><span class="sxs-lookup"><span data-stu-id="cd27b-123">You can also set the default mappings that are used when mapping data types between [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] and a non-[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] database management system (DBMS).</span></span> <span data-ttu-id="cd27b-124">詳しくは、「 [Data Type Mapping for Oracle Publishers](../non-sql/data-type-mapping-for-oracle-publishers.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="cd27b-124">For more information, see [Data Type Mapping for Oracle Publishers](../non-sql/data-type-mapping-for-oracle-publishers.md).</span></span>  
  
#### <a name="to-define-custom-data-type-mappings-when-creating-an-article-belonging-to-an-oracle-publication"></a><span data-ttu-id="cd27b-125">Oracle パブリケーションのアーティクル作成時にカスタム データ型マッピングを定義するには</span><span class="sxs-lookup"><span data-stu-id="cd27b-125">To define custom data type mappings when creating an article belonging to an Oracle publication</span></span>  
  
1.  <span data-ttu-id="cd27b-126">Oracle パブリケーションが存在しない場合は、Oracle パブリケーションを作成します。</span><span class="sxs-lookup"><span data-stu-id="cd27b-126">If one does not already exist, create an Oracle publication.</span></span>  
  
2.  <span data-ttu-id="cd27b-127">ディストリビューターで [sp_addarticle](/sql/relational-databases/system-stored-procedures/sp-addarticle-transact-sql)を実行します。</span><span class="sxs-lookup"><span data-stu-id="cd27b-127">At the Distributor, execute [sp_addarticle](/sql/relational-databases/system-stored-procedures/sp-addarticle-transact-sql).</span></span> <span data-ttu-id="cd27b-128">**\@use_default_datatypes** に **0** を指定します。</span><span class="sxs-lookup"><span data-stu-id="cd27b-128">Specify a value of **0** for **\@use_default_datatypes**.</span></span> <span data-ttu-id="cd27b-129">詳しくは、「 [アーティクルを定義](define-an-article.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="cd27b-129">For more information, see [Define an Article](define-an-article.md).</span></span>  
  
3.  <span data-ttu-id="cd27b-130">ディストリビューターで [sp_helparticlecolumns](/sql/relational-databases/system-stored-procedures/sp-helparticlecolumns-transact-sql) を実行して、パブリッシュ対象アーティクルに含まれる列の既存のマッピングを表示します。</span><span class="sxs-lookup"><span data-stu-id="cd27b-130">At the Distributor, execute [sp_helparticlecolumns](/sql/relational-databases/system-stored-procedures/sp-helparticlecolumns-transact-sql) to view the existing mapping for a column in a published article.</span></span>  
  
4.  <span data-ttu-id="cd27b-131">ディストリビューターで [sp_changearticlecolumndatatype](/sql/relational-databases/system-stored-procedures/sp-changearticlecolumndatatype-transact-sql)を実行します。</span><span class="sxs-lookup"><span data-stu-id="cd27b-131">At the Distributor, execute [sp_changearticlecolumndatatype](/sql/relational-databases/system-stored-procedures/sp-changearticlecolumndatatype-transact-sql).</span></span> <span data-ttu-id="cd27b-132">**\@publisher** に Oracle パブリッシャーの名前を指定し、 **\@publication**、 **\@article**、および **\@column** を指定して、パブリッシュする列を定義します。</span><span class="sxs-lookup"><span data-stu-id="cd27b-132">Specify the name of the Oracle Publisher for **\@publisher**, as well as **\@publication**, **\@article**, and **\@column** to define the published column.</span></span> <span data-ttu-id="cd27b-133">マップする [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] データ型名を **\@type** に指定し、該当する **\@length**、 **\@precision**、および **\@scale** を指定します。</span><span class="sxs-lookup"><span data-stu-id="cd27b-133">Specify the name of the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] data type to map to for **\@type**, as well as **\@length**, **\@precision**, and **\@scale**, where applicable.</span></span>  
  
5.  <span data-ttu-id="cd27b-134">ディストリビューターで [sp_articleview](/sql/relational-databases/system-stored-procedures/sp-articleview-transact-sql)を実行します。</span><span class="sxs-lookup"><span data-stu-id="cd27b-134">At the Distributor, execute [sp_articleview](/sql/relational-databases/system-stored-procedures/sp-articleview-transact-sql).</span></span> <span data-ttu-id="cd27b-135">これにより、Oracle パブリケーションからスナップショットを生成するときに使用するビューが作成されます。</span><span class="sxs-lookup"><span data-stu-id="cd27b-135">This creates the view used to generate the snapshot from the Oracle publication.</span></span>  
  
#### <a name="to-specify-a-mapping-as-the-default-mapping-for-a-data-type"></a><span data-ttu-id="cd27b-136">データ型に対する既定のマッピングを指定するには</span><span class="sxs-lookup"><span data-stu-id="cd27b-136">To specify a mapping as the default mapping for a data type</span></span>  
  
1.  <span data-ttu-id="cd27b-137">(省略可) ディストリビューターから任意のデータベースで [sp_getdefaultdatatypemapping](/sql/relational-databases/system-stored-procedures/sp-getdefaultdatatypemapping-transact-sql)を実行します。</span><span class="sxs-lookup"><span data-stu-id="cd27b-137">(Optional) At the Distributor on any database, execute [sp_getdefaultdatatypemapping](/sql/relational-databases/system-stored-procedures/sp-getdefaultdatatypemapping-transact-sql).</span></span> <span data-ttu-id="cd27b-138">**\@source_dbms**、 **\@source_type**、 **\@destination_dbms**、 **\@destination_version** を指定します。また、マップ元 DBMS を識別するために必要なパラメーターが他にもあれば、それらを指定してください。</span><span class="sxs-lookup"><span data-stu-id="cd27b-138">Specify **\@source_dbms**, **\@source_type**, **\@destination_dbms**, **\@destination_version**, and any other parameters needed to identify the source DBMS.</span></span> <span data-ttu-id="cd27b-139">マップ先 DBMS で現在マップされているデータ型の情報は、出力パラメーターを使って返されます。</span><span class="sxs-lookup"><span data-stu-id="cd27b-139">Information on the currently mapped data type in the destination DBMS is returned using the output parameters.</span></span>  
  
2.  <span data-ttu-id="cd27b-140">(省略可) ディストリビューター側の任意のデータベースに対して [sp_helpdatatypemap](/sql/relational-databases/system-stored-procedures/sp-helpdatatypemap-transact-sql)を実行します。</span><span class="sxs-lookup"><span data-stu-id="cd27b-140">(Optional) At the Distributor on any database, execute [sp_helpdatatypemap](/sql/relational-databases/system-stored-procedures/sp-helpdatatypemap-transact-sql).</span></span> <span data-ttu-id="cd27b-141">**\@source_dbms** を指定し、さらに、結果セットをフィルター選択するために必要なパラメーターが他にもあれば、それらを指定します。</span><span class="sxs-lookup"><span data-stu-id="cd27b-141">Specify **\@source_dbms** and any other parameters needed to filter the result set.</span></span> <span data-ttu-id="cd27b-142">目的のマッピングの **mapping_id** を結果セットで確認してください。</span><span class="sxs-lookup"><span data-stu-id="cd27b-142">Note the value of **mapping_id** for the desired mapping in the result set.</span></span>  
  
3.  <span data-ttu-id="cd27b-143">ディストリビューターから任意のデータベースで [sp_setdefaultdatatypemapping](/sql/relational-databases/system-stored-procedures/sp-setdefaultdatatypemapping-transact-sql)を実行します。</span><span class="sxs-lookup"><span data-stu-id="cd27b-143">At the Distributor on any database, execute [sp_setdefaultdatatypemapping](/sql/relational-databases/system-stored-procedures/sp-setdefaultdatatypemapping-transact-sql).</span></span>  
  
    -   <span data-ttu-id="cd27b-144">手順 2. で **mapping_id** の値を確認できた場合は、その値を **\@mapping_id** に指定します。</span><span class="sxs-lookup"><span data-stu-id="cd27b-144">If you know the desired value of **mapping_id** obtained in step 2, specify it for **\@mapping_id**.</span></span>  
  
    -   <span data-ttu-id="cd27b-145">**mapping_id** がわからない場合は、 **\@source_dbms**、 **\@source_type**、 **\@destination_dbms**、 **\@destination_type** の各パラメーターを指定し、さらに、既存のマッピングを識別するために必要なパラメーターが他にもあれば、それらを指定します。</span><span class="sxs-lookup"><span data-stu-id="cd27b-145">If you do not know the **mapping_id**, specify the parameters **\@source_dbms**, **\@source_type**, **\@destination_dbms**, **\@destination_type**, and any other parameters required to identify an existing mapping.</span></span>  
  
#### <a name="to-find-valid-data-types-for-a-given-oracle-data-type"></a><span data-ttu-id="cd27b-146">特定の Oracle データ型に対して有効なデータ型を見つけるには</span><span class="sxs-lookup"><span data-stu-id="cd27b-146">To find valid data types for a given Oracle data type</span></span>  
  
1.  <span data-ttu-id="cd27b-147">ディストリビューターから任意のデータベースで [sp_helpdatatypemap](/sql/relational-databases/system-stored-procedures/sp-helpdatatypemap-transact-sql)を実行します。</span><span class="sxs-lookup"><span data-stu-id="cd27b-147">At the Distributor on any database, execute [sp_helpdatatypemap](/sql/relational-databases/system-stored-procedures/sp-helpdatatypemap-transact-sql).</span></span> <span data-ttu-id="cd27b-148">**\@source_dbms** に **ORACLE** を指定し、さらに、結果セットをフィルター選択するために必要なパラメーターが他にもあれば、それらを指定します。</span><span class="sxs-lookup"><span data-stu-id="cd27b-148">Specify a value of **ORACLE** for **\@source_dbms** and any other parameters needed to filter the result set.</span></span>  
  
###  <a name="examples-transact-sql"></a><a name="TsqlExample"></a> <span data-ttu-id="cd27b-149">例 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="cd27b-149">Examples (Transact-SQL)</span></span>  
 <span data-ttu-id="cd27b-150">次の例では、Oracle のデータ型 NUMBER の列を [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のデータ型にマップします。既定では、`numeric` データ型にマップされますが、ここでは、`float`(38,38) にマップしています。</span><span class="sxs-lookup"><span data-stu-id="cd27b-150">This example changes a column with an Oracle data type of NUMBER so it is mapped to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] data type `numeric`(38,38), instead of the default data type `float`.</span></span>  
  
 [!code-sql[HowTo#sp_changecolumndatatype](../../../snippets/tsql/SQL15/replication/howto/tsql/datatypemapping.sql#sp_changecolumndatatype)]  
  
 <span data-ttu-id="cd27b-151">次のクエリの例では、Oracle 9 データ型の `CHAR` について、既定のマッピングと代替マッピングを返します。</span><span class="sxs-lookup"><span data-stu-id="cd27b-151">This example query returns the default and alternative mappings for the Oracle 9 data type `CHAR`.</span></span>  
  
 [!code-sql[HowTo#sp_helpcolumndatatype_char](../../../snippets/tsql/SQL15/replication/howto/tsql/datatypemapping.sql#sp_helpcolumndatatype_char)]  
  
 <span data-ttu-id="cd27b-152">次のクエリの例では、Oracle 9 データ型の `NUMBER` で、小数点以下桁数または有効桁数を指定しなかった場合に使用される既定のマッピングを返します。</span><span class="sxs-lookup"><span data-stu-id="cd27b-152">This example query returns the default mappings for the Oracle 9 data type `NUMBER` when it is specified without a scale or precision.</span></span>  
  
 [!code-sql[HowTo#sp_helpcolumndatatype_number](../../../snippets/tsql/SQL15/replication/howto/tsql/datatypemapping.sql#sp_helpcolumndatatype_number)]  
  
## <a name="see-also"></a><span data-ttu-id="cd27b-153">参照</span><span class="sxs-lookup"><span data-stu-id="cd27b-153">See Also</span></span>  
 <span data-ttu-id="cd27b-154">[Data Type Mapping for Oracle Publishers](../non-sql/data-type-mapping-for-oracle-publishers.md) </span><span class="sxs-lookup"><span data-stu-id="cd27b-154">[Data Type Mapping for Oracle Publishers](../non-sql/data-type-mapping-for-oracle-publishers.md) </span></span>  
 <span data-ttu-id="cd27b-155">[異種データベース レプリケーション](../non-sql/heterogeneous-database-replication.md) </span><span class="sxs-lookup"><span data-stu-id="cd27b-155">[Heterogeneous Database Replication](../non-sql/heterogeneous-database-replication.md) </span></span>  
 <span data-ttu-id="cd27b-156">[Replication System Stored Procedures Concepts](../concepts/replication-system-stored-procedures-concepts.md) </span><span class="sxs-lookup"><span data-stu-id="cd27b-156">[Replication System Stored Procedures Concepts](../concepts/replication-system-stored-procedures-concepts.md) </span></span>  
 [<span data-ttu-id="cd27b-157">Oracle パブリッシャーの構成</span><span class="sxs-lookup"><span data-stu-id="cd27b-157">Configure an Oracle Publisher</span></span>](../non-sql/configure-an-oracle-publisher.md)  
  
  
