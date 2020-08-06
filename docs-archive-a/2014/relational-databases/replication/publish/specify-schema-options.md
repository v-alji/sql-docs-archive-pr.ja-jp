---
title: スキーマ オプションの指定 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- schemas [SQL Server replication], options
- articles [SQL Server replication], transactional replication options
- articles [SQL Server replication], merge replication options
- articles [SQL Server replication], schema options
ms.assetid: 1f85a479-bd6e-4023-abf7-7435a7e5b567
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 52064cc189dc62152814436d2d11326a74c89ff6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87719850"
---
# <a name="specify-schema-options"></a><span data-ttu-id="16cfb-102">スキーマ オプションの指定</span><span class="sxs-lookup"><span data-stu-id="16cfb-102">Specify Schema Options</span></span>
  <span data-ttu-id="16cfb-103">このトピックでは、 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] で [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[tsql](../../../includes/tsql-md.md)]を使用して、スキーマのオプションを指定する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="16cfb-103">This topic describes how to specify schema options in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../../includes/tsql-md.md)].</span></span> <span data-ttu-id="16cfb-104">テーブルまたはビューをパブリッシュするとき、パブリッシュされたオブジェクト用にレプリケートされるオブジェクトの作成オプションを制御できます。</span><span class="sxs-lookup"><span data-stu-id="16cfb-104">When you are publishing a table or view, you can control the object creation options that are replicated for the published object.</span></span> <span data-ttu-id="16cfb-105">アーティクルが作成されるときにこれらのオプションを設定することができ、後で変更することもできます。</span><span class="sxs-lookup"><span data-stu-id="16cfb-105">You can set these option when the article is created, and you can also change them at a later time.</span></span> <span data-ttu-id="16cfb-106">アーティクルに対してオプションを明示的に指定しなかった場合、既定のオプションが定義されます。</span><span class="sxs-lookup"><span data-stu-id="16cfb-106">If you do not explicitly specify these options for an article, a default set of options will be defined.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="16cfb-107">レプリケーションのストアド プロシージャを使用した場合の既定のスキーマ オプションは、 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]を使ってアーティクルを追加するときの既定のオプションとは異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="16cfb-107">The default schema options when using replication stored procedures may differ from the default options when articles are added using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="16cfb-108">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="16cfb-108">**In This Topic**</span></span>  
  
-   <span data-ttu-id="16cfb-109">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="16cfb-109">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="16cfb-110">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="16cfb-110">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="16cfb-111">Recommendations (推奨事項)</span><span class="sxs-lookup"><span data-stu-id="16cfb-111">Recommendations</span></span>](#Recommendations)  
  
-   <span data-ttu-id="16cfb-112">**スキーマ オプションを指定するために使用するもの:**</span><span class="sxs-lookup"><span data-stu-id="16cfb-112">**To specify schema options, using:**</span></span>  
  
     [<span data-ttu-id="16cfb-113">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="16cfb-113">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="16cfb-114">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="16cfb-114">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="16cfb-115">はじめに</span><span class="sxs-lookup"><span data-stu-id="16cfb-115">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="16cfb-116">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="16cfb-116">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="16cfb-117">パブリケーションの作成後にスキーマ オプションを変更する場合は、新しいスナップショットを生成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="16cfb-117">If you change schema options after a publication is created, you must generate a new snapshot.</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="16cfb-118">推奨事項</span><span class="sxs-lookup"><span data-stu-id="16cfb-118">Recommendations</span></span>  
  
-   <span data-ttu-id="16cfb-119">スキーマオプションの完全な一覧については、 [sp_addarticle &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-addarticle-transact-sql)の\*\* \@ schema_option\*\*パラメーターと sp_addmergearticle &#40;[transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="16cfb-119">For the complete list of schema options, see the **\@schema_option** parameter of [sp_addarticle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addarticle-transact-sql) and [sp_addmergearticle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="16cfb-120">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="16cfb-120">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="16cfb-121">スキーマ オプション (制約やトリガーをサブスクライバーにコピーするかどうかなど) は、 **[アーティクルのプロパティ - \<Article>]** ダイアログ ボックスの **[プロパティ]** タブで指定します。</span><span class="sxs-lookup"><span data-stu-id="16cfb-121">Specify schema options, such as whether to copy constraints and triggers to Subscribers, on the **Properties** tab of the **Article Properties - \<Article>** dialog box.</span></span> <span data-ttu-id="16cfb-122">このタブは、パブリケーションの新規作成ウィザードおよび **[パブリケーションのプロパティ - \<Publication>]** ダイアログ ボックスで使用できます。</span><span class="sxs-lookup"><span data-stu-id="16cfb-122">This tab is available in the New Publication Wizard and the **Publication Properties - \<Publication>** dialog box.</span></span> <span data-ttu-id="16cfb-123">ウィザードの使用およびダイアログ ボックスへのアクセスの詳細については、「[パブリケーションの作成](create-a-publication.md)」および「[View and Modify Publication Properties](view-and-modify-publication-properties.md)」 (パブリケーション プロパティの表示および変更) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="16cfb-123">For more information about using the wizard and accessing the dialog box, see [Create a Publication](create-a-publication.md) and [View and Modify Publication Properties](view-and-modify-publication-properties.md).</span></span>  
  
#### <a name="to-specify-schema-options"></a><span data-ttu-id="16cfb-124">スキーマ オプションを指定するには</span><span class="sxs-lookup"><span data-stu-id="16cfb-124">To specify schema options</span></span>  
  
1.  <span data-ttu-id="16cfb-125">パブリケーションの新規作成ウィザードまたは **[パブリケーションのプロパティ - \<Publication>]** ダイアログ ボックスの **[アーティクル]** ページで、アーティクルを選択し、 **[アーティクルのプロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="16cfb-125">On the **Articles** Page of the New Publication Wizard or **Publication Properties - \<Publication>** dialog box, select an article, and then click **Article Properties**.</span></span>  
  
2.  <span data-ttu-id="16cfb-126">スキーマ オプションの変更を適用するアーティクルを選択します。</span><span class="sxs-lookup"><span data-stu-id="16cfb-126">Select which articles schema option changes should apply to:</span></span>  
  
    -   <span data-ttu-id="16cfb-127">**[反転表示された \<ObjectType> アーティクルのプロパティを設定]** をクリックして、 **[アーティクルのプロパティ - \<ObjectName>]** ダイアログ ボックスを表示します。このダイアログ ボックスで行われたプロパティの変更は、 **[アーティクル]** ページのオブジェクト ペインで反転表示されたオブジェクトのみに適用されます。</span><span class="sxs-lookup"><span data-stu-id="16cfb-127">Click **Set Properties of Highlighted \<ObjectType> Article** to launch the **Article Properties - \<ObjectName>** dialog box; property changes made in this dialog box are applied only to the object that is highlighted in the object pane on the **Articles** page.</span></span>  
  
    -   <span data-ttu-id="16cfb-128">**[すべての\<ObjectType> アーティクルのプロパティを設定]** をクリックして、 **[すべての \<ObjectType> アーティクルのプロパティ]** ダイアログ ボックスを表示します。このダイアログ ボックスで行われたプロパティの変更は、パブリケーション用に選択されていないオブジェクトも含め、 **[アーティクル]** ページのオブジェクト ペインにあるこの種類のすべてのオブジェクトに適用されます。</span><span class="sxs-lookup"><span data-stu-id="16cfb-128">Click **Set Properties of All \<ObjectType> Articles** to launch the **Properties for All \<ObjectType> Articles** dialog box; property changes made in this dialog box are applied to all objects of that type in the object pane on the **Articles** page, including ones not yet selected for publication.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="16cfb-129">**[すべての \<ObjectType> アーティクルのプロパティ]** ダイアログ ボックスで行われたプロパティの変更は、 **[アーティクルのプロパティ - \<ObjectName>]** ダイアログ ボックスで以前行われた変更をすべてオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="16cfb-129">Property changes made in the **Properties for All \<ObjectType> Articles** dialog box override any made previously in the **Article Properties - \<ObjectName>** dialog box.</span></span> <span data-ttu-id="16cfb-130">たとえば、あるオブジェクトの種類のすべてのアーティクルに対して複数の既定を設定し、かつそれぞれのオブジェクトに対してプロパティを設定する場合には、最初にすべてのアーティクルに対する既定を設定します。</span><span class="sxs-lookup"><span data-stu-id="16cfb-130">If, for example, you want to set a number of defaults for all articles of an object type, but also want to set some properties for individual objects, set the defaults for all articles first.</span></span> <span data-ttu-id="16cfb-131">次に、それぞれのオブジェクトに対してプロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="16cfb-131">Then set the properties for the individual objects.</span></span>  
  
3.  <span data-ttu-id="16cfb-132">**[アーティクルのプロパティ - \<Article>]** ダイアログ ボックスの **[プロパティ]** タブの **[サブスクライバーへのオブジェクトと設定のコピー]** および **[対象オブジェクト]** セクションで、オプションの値を設定します。</span><span class="sxs-lookup"><span data-stu-id="16cfb-132">In the **Copy Objects and Settings to Subscriber** and **Destination Object** sections of the **Properties** tab of the **Article Properties - \<Article>** dialog box, specify values for the options.</span></span>  
  
4.  <span data-ttu-id="16cfb-133">必要に応じてプロパティを変更し、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="16cfb-133">Modify any properties if necessary, and then click **OK**.</span></span>  
  
5.  <span data-ttu-id="16cfb-134">**[パブリケーションのプロパティ - \<Publication>]** ダイアログ ボックスが表示されている場合は、 **[OK]** をクリックして保存し、ダイアログ ボックスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="16cfb-134">If you are in the **Publication Properties - \<Publication>** dialog box, click **OK** to save and close the dialog box.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="16cfb-135">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="16cfb-135">Using Transact-SQL</span></span>  
 <span data-ttu-id="16cfb-136">スキーマ オプションは、1 つまたは複数のオプションについて、 [| (ビット演算 OR)](/sql/t-sql/language-elements/bitwise-or-transact-sql) を実行した結果を 16 進数値で指定します。</span><span class="sxs-lookup"><span data-stu-id="16cfb-136">Schema options are specified as a hexadecimal value that is the [| (Bitwise OR)](/sql/t-sql/language-elements/bitwise-or-transact-sql) result of one or more options.</span></span> <span data-ttu-id="16cfb-137">詳細については、「 [sp_addarticle](/sql/relational-databases/system-stored-procedures/sp-addarticle-transact-sql) 」および「 [sp_addmergearticle](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="16cfb-137">For more information, see [sp_addarticle](/sql/relational-databases/system-stored-procedures/sp-addarticle-transact-sql) and [sp_addmergearticle](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="16cfb-138">ビットごとの演算を実行する際は、あらかじめ、スキーマ オプションの値を **binary** から **int** に変換しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="16cfb-138">You must convert schema option values from **binary** to **int** before performing a bitwise operation.</span></span> <span data-ttu-id="16cfb-139">詳細については、「[CAST and CONVERT &#40;Transact-SQL&#41;](/sql/t-sql/functions/cast-and-convert-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="16cfb-139">For more information, see [CAST and CONVERT &#40;Transact-SQL&#41;](/sql/t-sql/functions/cast-and-convert-transact-sql).</span></span>  
  
#### <a name="to-specify-schema-options-when-defining-an-article-for-a-snapshot-or-transactional-publication"></a><span data-ttu-id="16cfb-140">スナップショット パブリケーションまたはトランザクション パブリケーションのアーティクルを定義するときにスキーマ オプションを指定するには</span><span class="sxs-lookup"><span data-stu-id="16cfb-140">To specify schema options when defining an article for a snapshot or transactional publication</span></span>  
  
1.  <span data-ttu-id="16cfb-141">パブリッシャー側のパブリケーション データベースに対して、 [sp_addarticle](/sql/relational-databases/system-stored-procedures/sp-addarticle-transact-sql)を実行します。</span><span class="sxs-lookup"><span data-stu-id="16cfb-141">At the Publisher on the publication database, execute [sp_addarticle](/sql/relational-databases/system-stored-procedures/sp-addarticle-transact-sql).</span></span> <span data-ttu-id="16cfb-142">\*\* \@ パブリケーション**のアーティクルが属しているパブリケーションの名前、 \*\* \@ アーティクルのアーティクルの名前、** \*\* \@ source_object**にパブリッシュするデータベースオブジェクト、 \*\* \@ 種類**としてデータベースオブジェクトの種類、| を指定します。 [(ビットごとの OR)](/sql/t-sql/language-elements/bitwise-or-transact-sql)\*\* \@ schema_option\*\*の1つ以上のスキーマオプションの結果。</span><span class="sxs-lookup"><span data-stu-id="16cfb-142">Specify the name of the publication to which the article belongs for **\@publication**, a name for the article for **\@article**, the database object being published for **\@source_object**, the type of database object for **\@type**, and the [| (Bitwise OR)](/sql/t-sql/language-elements/bitwise-or-transact-sql) result of one or more schema options for **\@schema_option**.</span></span> <span data-ttu-id="16cfb-143">詳しくは、「 [アーティクルを定義](define-an-article.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="16cfb-143">For more information, see [Define an Article](define-an-article.md).</span></span>  
  
#### <a name="to-specify-schema-options-when-defining-an-article-for-a-merge-publication"></a><span data-ttu-id="16cfb-144">マージ パブリケーションのアーティクルを定義するときにスキーマ オプションを指定するには</span><span class="sxs-lookup"><span data-stu-id="16cfb-144">To specify schema options when defining an article for a merge publication</span></span>  
  
1.  <span data-ttu-id="16cfb-145">パブリッシャー側のパブリケーション データベースに対して、 [sp_addmergearticle](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql)を実行します。</span><span class="sxs-lookup"><span data-stu-id="16cfb-145">At the Publisher on the publication database, execute [sp_addmergearticle](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql).</span></span> <span data-ttu-id="16cfb-146">\*\* \@ パブリケーション**のアーティクルが属しているパブリケーションの名前、**アーティクルのアーティクル名、 \@ \*\* \*\* \@ source_object**にパブリッシュするデータベースオブジェクト、および | を指定します。 [(ビットごとの OR)](/sql/t-sql/language-elements/bitwise-or-transact-sql)** \@ schema_option\*\*の1つ以上のスキーマオプションの結果。</span><span class="sxs-lookup"><span data-stu-id="16cfb-146">Specify the name of the publication to which the article belongs for **\@publication**, a name for the article for **\@article**, the database object being published for **\@source_object**, and the [| (Bitwise OR)](/sql/t-sql/language-elements/bitwise-or-transact-sql) result of one or more schema options for **\@schema_option**.</span></span> <span data-ttu-id="16cfb-147">詳しくは、「 [アーティクルを定義](define-an-article.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="16cfb-147">For more information, see [Define an Article](define-an-article.md).</span></span>  
  
#### <a name="to-change-schema-options-for-an-existing-article-in-a-snapshot-or-transactional-publication"></a><span data-ttu-id="16cfb-148">スナップショット パブリケーションまたはトランザクション パブリケーションの既存のアーティクルに設定されているスキーマ オプションを変更するには</span><span class="sxs-lookup"><span data-stu-id="16cfb-148">To change schema options for an existing article in a snapshot or transactional publication</span></span>  
  
1.  <span data-ttu-id="16cfb-149">パブリッシャー側のパブリケーション データベースに対して [sp_helparticle](/sql/relational-databases/system-stored-procedures/sp-helparticle-transact-sql)を実行します。</span><span class="sxs-lookup"><span data-stu-id="16cfb-149">At the Publisher on the publication database, execute [sp_helparticle](/sql/relational-databases/system-stored-procedures/sp-helparticle-transact-sql).</span></span> <span data-ttu-id="16cfb-150">\*\* \@ パブリケーション**のアーティクルが属しているパブリケーションの名前と、アーティクルのアーティクルの名前を指定し** \@ ます。\*\*</span><span class="sxs-lookup"><span data-stu-id="16cfb-150">Specify the name of the publication to which the article belongs for **\@publication** and the name of the article for **\@article**.</span></span> <span data-ttu-id="16cfb-151">結果セットの **schema_option** 列の値を確認してください。</span><span class="sxs-lookup"><span data-stu-id="16cfb-151">Note the value of the **schema_option** column in the result set.</span></span>  
  
2.  <span data-ttu-id="16cfb-152">手順 1 の値、および必要なスキーマ オプションの値を使って [& (ビット演算 AND)](/sql/t-sql/language-elements/bitwise-and-transact-sql) 演算を実行し、対象のオプションが設定されているかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="16cfb-152">Execute a [& (Bitwise AND)](/sql/t-sql/language-elements/bitwise-and-transact-sql) operation using the value from step 1 and the desired schema option value to determine if the option is set.</span></span>  
  
    -   <span data-ttu-id="16cfb-153">実行結果が **0**の場合、オプションは設定されていません。</span><span class="sxs-lookup"><span data-stu-id="16cfb-153">If the result is **0**, the option is not set.</span></span>  
  
    -   <span data-ttu-id="16cfb-154">実行結果がオプションの値の場合、そのオプションは既に設定されています。</span><span class="sxs-lookup"><span data-stu-id="16cfb-154">If the result is the option value, the option is already set.</span></span>  
  
3.  <span data-ttu-id="16cfb-155">オプションが設定されていなかった場合は、手順 1. の値と、必要なスキーマ オプション値を使って [| (ビット演算 OR)](/sql/t-sql/language-elements/bitwise-or-transact-sql) 演算を実行します。</span><span class="sxs-lookup"><span data-stu-id="16cfb-155">If the option is not set, execute a [| (Bitwise OR)](/sql/t-sql/language-elements/bitwise-or-transact-sql) operation using the value from step 1 and the desired schema option value.</span></span>  
  
4.  <span data-ttu-id="16cfb-156">パブリッシャーのパブリケーション データベースで [sp_changearticle](/sql/relational-databases/system-stored-procedures/sp-changearticle-transact-sql)を実行します。</span><span class="sxs-lookup"><span data-stu-id="16cfb-156">At the Publisher on the publication database, execute [sp_changearticle](/sql/relational-databases/system-stored-procedures/sp-changearticle-transact-sql).</span></span> <span data-ttu-id="16cfb-157">\*\* \@ パブリケーション**のアーティクルが属しているパブリケーションの名前 **、アーティクルの \@ **アーティクル名、 \*\* \@ プロパティ**に**schema_option**の値、および手順 3. の16進数の結果を [ \*\* \@ 値\*\*] に指定します。</span><span class="sxs-lookup"><span data-stu-id="16cfb-157">Specify the name of the publication to which the article belongs for **\@publication**, the name of the article for **\@article**, a value of **schema_option** for **\@property**, and the hexadecimal result from step 3 for **\@value**.</span></span>  
  
5.  <span data-ttu-id="16cfb-158">スナップショット エージェントを実行して、新しいスナップショットを生成します。</span><span class="sxs-lookup"><span data-stu-id="16cfb-158">Run the Snapshot Agent to generate a new snapshot.</span></span> <span data-ttu-id="16cfb-159">詳しくは、「 [初期スナップショットの作成および適用](../create-and-apply-the-initial-snapshot.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="16cfb-159">For more information, see [Create and Apply the Initial Snapshot](../create-and-apply-the-initial-snapshot.md).</span></span>  
  
#### <a name="to-change-schema-options-for-an-existing-article-in-a-merge-publication"></a><span data-ttu-id="16cfb-160">マージ パブリケーションの既存のアーティクルのスキーマ オプションを変更するには</span><span class="sxs-lookup"><span data-stu-id="16cfb-160">To change schema options for an existing article in a merge publication</span></span>  
  
1.  <span data-ttu-id="16cfb-161">パブリッシャーのパブリケーション データベースで [sp_helpmergearticle](/sql/relational-databases/system-stored-procedures/sp-helpmergearticle-transact-sql)を実行します。</span><span class="sxs-lookup"><span data-stu-id="16cfb-161">At the Publisher on the publication database, execute [sp_helpmergearticle](/sql/relational-databases/system-stored-procedures/sp-helpmergearticle-transact-sql).</span></span> <span data-ttu-id="16cfb-162">\*\* \@ パブリケーション**のアーティクルが属しているパブリケーションの名前と、アーティクルのアーティクルの名前を指定し** \@ ます。\*\*</span><span class="sxs-lookup"><span data-stu-id="16cfb-162">Specify the name of the publication to which the article belongs for **\@publication** and the name of the article for **\@article**.</span></span> <span data-ttu-id="16cfb-163">結果セットの **schema_option** 列の値を確認してください。</span><span class="sxs-lookup"><span data-stu-id="16cfb-163">Note the value of the **schema_option** column in the result set.</span></span>  
  
2.  <span data-ttu-id="16cfb-164">手順 1 の値、および必要なスキーマ オプションの値を使って [& (ビット演算 AND)](/sql/t-sql/language-elements/bitwise-and-transact-sql) 演算を実行し、対象のオプションが設定されているかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="16cfb-164">Execute a [& (Bitwise AND)](/sql/t-sql/language-elements/bitwise-and-transact-sql) operation using the value from step 1 and the desired schema option value to determine if the option is set.</span></span>  
  
    -   <span data-ttu-id="16cfb-165">実行結果が **0**の場合、オプションは設定されていません。</span><span class="sxs-lookup"><span data-stu-id="16cfb-165">If the result is **0**, the option is not set.</span></span>  
  
    -   <span data-ttu-id="16cfb-166">実行結果がオプションの値の場合、そのオプションは既に設定されています。</span><span class="sxs-lookup"><span data-stu-id="16cfb-166">If the result is the option value, the option is already set.</span></span>  
  
3.  <span data-ttu-id="16cfb-167">オプションが設定されていなかった場合は、手順 1. の値と、必要なスキーマ オプション値を使って [| (ビット演算 OR)](/sql/t-sql/language-elements/bitwise-or-transact-sql) 演算を実行します。</span><span class="sxs-lookup"><span data-stu-id="16cfb-167">If the option is not set, execute a [| (Bitwise OR)](/sql/t-sql/language-elements/bitwise-or-transact-sql) operation using the value from step 1 and the desired schema option value.</span></span>  
  
4.  <span data-ttu-id="16cfb-168">パブリッシャー側のパブリケーション データベースに対して、 [sp_changemergearticle](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql)を実行します。</span><span class="sxs-lookup"><span data-stu-id="16cfb-168">At the Publisher on the publication database, execute [sp_changemergearticle](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql).</span></span> <span data-ttu-id="16cfb-169">\*\* \@ パブリケーション**のアーティクルが属しているパブリケーションの名前 **、アーティクルの \@ **アーティクル名、 \*\* \@ プロパティ**に**schema_option**の値、および手順 3. の16進数の結果を [ \*\* \@ 値\*\*] に指定します。</span><span class="sxs-lookup"><span data-stu-id="16cfb-169">Specify the name of the publication to which the article belongs for **\@publication**, the name of the article for **\@article**, a value of **schema_option** for **\@property**, and the hexadecimal result from step 3 for **\@value**.</span></span>  
  
5.  <span data-ttu-id="16cfb-170">スナップショット エージェントを実行して、新しいスナップショットを生成します。</span><span class="sxs-lookup"><span data-stu-id="16cfb-170">Run the Snapshot Agent to generate a new snapshot.</span></span> <span data-ttu-id="16cfb-171">詳しくは、「 [初期スナップショットの作成および適用](../create-and-apply-the-initial-snapshot.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="16cfb-171">For more information, see [Create and Apply the Initial Snapshot](../create-and-apply-the-initial-snapshot.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16cfb-172">参照</span><span class="sxs-lookup"><span data-stu-id="16cfb-172">See Also</span></span>  
 <span data-ttu-id="16cfb-173">[データとデータベース オブジェクトのパブリッシュ](publish-data-and-database-objects.md) </span><span class="sxs-lookup"><span data-stu-id="16cfb-173">[Publish Data and Database Objects](publish-data-and-database-objects.md) </span></span>  
 [<span data-ttu-id="16cfb-174">Article Options for Transactional Replication</span><span class="sxs-lookup"><span data-stu-id="16cfb-174">Article Options for Transactional Replication</span></span>](../transactional/article-options-for-transactional-replication.md)  
  
  
