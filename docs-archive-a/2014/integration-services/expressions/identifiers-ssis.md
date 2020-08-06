---
title: 識別子 (SSIS) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- regular identifiers [Integration Services]
- variables [Integration Services], expressions
- identifiers [Integration Services]
- expressions [Integration Services], variables
- lineage identifiers
- columns [Integration Services], identifiers
- names [Integration Services]
- expressions [Integration Services], identifiers
- qualified identifiers [Integration Services]
ms.assetid: 56af984d-88b4-4db8-b6a2-6b07315a699e
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 751830d30f26e9b182b3b926549760d1df517914
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87716526"
---
# <a name="identifiers-ssis"></a><span data-ttu-id="bf2e9-102">識別子 (SSIS)</span><span class="sxs-lookup"><span data-stu-id="bf2e9-102">Identifiers (SSIS)</span></span>
  <span data-ttu-id="bf2e9-103">識別子とは、式の内部で演算に使用できる列および変数のことです。</span><span class="sxs-lookup"><span data-stu-id="bf2e9-103">In expressions, identifiers are columns and variables that are available to the operation.</span></span> <span data-ttu-id="bf2e9-104">式では、標準識別子と修飾された識別子を使用できます。</span><span class="sxs-lookup"><span data-stu-id="bf2e9-104">Expressions can use regular and qualified identifiers.</span></span>  
  
## <a name="regular-identifiers"></a><span data-ttu-id="bf2e9-105">標準識別子</span><span class="sxs-lookup"><span data-stu-id="bf2e9-105">Regular Identifiers</span></span>  
 <span data-ttu-id="bf2e9-106">標準識別子とは、追加の修飾子を必要としない識別子のことです。</span><span class="sxs-lookup"><span data-stu-id="bf2e9-106">A regular identifier is an identifier that needs no additional qualifiers.</span></span> <span data-ttu-id="bf2e9-107">たとえば、 **MiddleName**は、 **AdventureWorks** データベースの **Contacts** テーブルの列ですが、これは標準識別子です。</span><span class="sxs-lookup"><span data-stu-id="bf2e9-107">For example, **MiddleName**, a column in the **Contacts** table of the **AdventureWorks** database, is a regular identifier.</span></span>  
  
 <span data-ttu-id="bf2e9-108">標準識別子の名前付けは、次の規則に従う必要があります。</span><span class="sxs-lookup"><span data-stu-id="bf2e9-108">The naming of regular identifiers must follow these rules:</span></span>  
  
-   <span data-ttu-id="bf2e9-109">名前の最初の文字は、Unicode Standard 2.0 で定義されている文字か、アンダースコア (_) である必要があります。</span><span class="sxs-lookup"><span data-stu-id="bf2e9-109">The first character of the name must be a letter as defined by the Unicode Standard 2.0, or an underscore (_).</span></span>  
  
-   <span data-ttu-id="bf2e9-110">2 番目以降の文字では、Unicode Standard 2.0 に定義されている文字または数字と、アンダースコア (_)、\@、$、および # 文字を使用できます。</span><span class="sxs-lookup"><span data-stu-id="bf2e9-110">Subsequent characters can be letters or numbers as defined in the Unicode Standard 2.0, the underscore (_), \@, $, and # characters.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="bf2e9-111">埋め込み型スペース、および上記の一覧に表示されていない特殊文字は、標準識別子では無効です。</span><span class="sxs-lookup"><span data-stu-id="bf2e9-111">Embedded spaces and special characters, other than the ones listed, are not valid in regular identifiers.</span></span> <span data-ttu-id="bf2e9-112">スペースや特殊文字を使用するには、標準識別子ではなく修飾された識別子を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="bf2e9-112">In order to use spaces and special characters, you must use a qualified identifier instead of a regular identifier.</span></span>  
  
## <a name="qualified-identifiers"></a><span data-ttu-id="bf2e9-113">修飾された識別子</span><span class="sxs-lookup"><span data-stu-id="bf2e9-113">Qualified Identifiers</span></span>  
 <span data-ttu-id="bf2e9-114">修飾された識別子とは、角かっこで区切られた識別子のことです。</span><span class="sxs-lookup"><span data-stu-id="bf2e9-114">A qualified identifier is an identifier that is delimited by brackets.</span></span> <span data-ttu-id="bf2e9-115">識別子の名前にスペースが含まれていたり、識別子名の最初の文字が英字でなかったり、アンダースコアの場合、識別子には区切り記号が必要になります。</span><span class="sxs-lookup"><span data-stu-id="bf2e9-115">An identifier may require a delimiter because the name of the identifier includes spaces, or because the identifier name does not begin with either a letter or the underscore character.</span></span> <span data-ttu-id="bf2e9-116">たとえば、列名 **Middle Name** は角かっこで修飾し、式では [Middle Name] と記述する必要があります。</span><span class="sxs-lookup"><span data-stu-id="bf2e9-116">For example, the column name **Middle Name** must be qualified by brackets and written as [Middle Name] in an expression.</span></span>  
  
 <span data-ttu-id="bf2e9-117">識別子の名前にスペースが含まれる場合、または標準識別子の名前が有効でない場合は、識別子を修飾する必要があります。</span><span class="sxs-lookup"><span data-stu-id="bf2e9-117">If the name of the identifier includes spaces, or if the name is not a valid regular identifier name, the identifier must be qualified.</span></span> <span data-ttu-id="bf2e9-118">式エバリュエーターは、角かっこ ([]) を使用して識別子を修飾します。</span><span class="sxs-lookup"><span data-stu-id="bf2e9-118">The expression evaluator uses the opening and closing ([]) brackets to qualify identifiers.</span></span> <span data-ttu-id="bf2e9-119">角かっこは、文字列の最初と最後に配置します。</span><span class="sxs-lookup"><span data-stu-id="bf2e9-119">The brackets are put in the first and the last position of the string.</span></span> <span data-ttu-id="bf2e9-120">たとえば、識別子 5$> は [5$>] になります。</span><span class="sxs-lookup"><span data-stu-id="bf2e9-120">For example, the identifier 5$> becomes [5$>].</span></span> <span data-ttu-id="bf2e9-121">角かっこは、列名、変数名、関数名で使用できます。</span><span class="sxs-lookup"><span data-stu-id="bf2e9-121">Brackets can be used with column names, variable names, and function names.</span></span>  
  
 <span data-ttu-id="bf2e9-122">[!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーのダイアログ ボックスを使用して式を構築する場合、標準識別子は、自動的に角かっこで囲まれます。</span><span class="sxs-lookup"><span data-stu-id="bf2e9-122">If you build expressions using the [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer dialog boxes, regular identifiers are automatically enclosed in brackets.</span></span> <span data-ttu-id="bf2e9-123">ただし、角かっこが必要となるのは、名前に無効な文字が含まれている場合のみです。</span><span class="sxs-lookup"><span data-stu-id="bf2e9-123">However, brackets are required only if the name include invalid characters.</span></span> <span data-ttu-id="bf2e9-124">たとえば、 **MiddleName** という名前の列は、角かっこなしでも有効です。</span><span class="sxs-lookup"><span data-stu-id="bf2e9-124">For example, the column named **MiddleName** is valid without brackets.</span></span>  
  
 <span data-ttu-id="bf2e9-125">式の内部では、角かっこが含まれる列名を参照できません。</span><span class="sxs-lookup"><span data-stu-id="bf2e9-125">You cannot reference column names that include brackets in expressions.</span></span> <span data-ttu-id="bf2e9-126">たとえば、列名 **Column[1]** は、式では使用できません。</span><span class="sxs-lookup"><span data-stu-id="bf2e9-126">For example, the column name **Column[1]** cannot be used in an expression.</span></span> <span data-ttu-id="bf2e9-127">この列を式で使用するには、角かっこなしの名前に変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="bf2e9-127">To use the column in an expression it must be renamed to a name without brackets.</span></span>  
  
## <a name="lineage-identifiers"></a><span data-ttu-id="bf2e9-128">系列 ID</span><span class="sxs-lookup"><span data-stu-id="bf2e9-128">Lineage Identifiers</span></span>  
 <span data-ttu-id="bf2e9-129">式では、系列 ID を使用して列を参照できます。</span><span class="sxs-lookup"><span data-stu-id="bf2e9-129">Expressions can use lineage identifiers to refer to columns.</span></span> <span data-ttu-id="bf2e9-130">系列 ID は、最初にパッケージを作成する際に自動的に割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="bf2e9-130">The lineage identifiers are assigned automatically when you first create the package.</span></span> <span data-ttu-id="bf2e9-131">列の系列 ID は、 **デザイナーにある、** [詳細エディター] **ダイアログ ボックスの** [列のプロパティ] [!INCLUDE[ssIS](../../includes/ssis-md.md)] タブで表示できます。</span><span class="sxs-lookup"><span data-stu-id="bf2e9-131">You can view the lineage identifier for a column on the **Column Properties** tab of the **Advanced Editor** dialog box in the [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer.</span></span>  
  
 <span data-ttu-id="bf2e9-132">列の系列 ID を使用してその列を参照する場合、系列 ID に、ポンド (#) 記号のプレフィックスを含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="bf2e9-132">If you refer to a column using its lineage identifier, the identifier must include the pound (#) character prefix.</span></span> <span data-ttu-id="bf2e9-133">たとえば、系列 ID が 147 の列は、#147 として参照する必要があります。</span><span class="sxs-lookup"><span data-stu-id="bf2e9-133">For example, a column with the lineage identifier 147 must be referenced as #147.</span></span>  
  
 <span data-ttu-id="bf2e9-134">式が正常に解析された場合、式エバリュエーターは、ダイアログ ボックス内の系列 ID を列名に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="bf2e9-134">If an expression parses successfully, the expression evaluator replaces the lineage identifiers with column names in the dialog box.</span></span>  
  
## <a name="unique-column-names"></a><span data-ttu-id="bf2e9-135">一意の列名</span><span class="sxs-lookup"><span data-stu-id="bf2e9-135">Unique Column Names</span></span>  
 <span data-ttu-id="bf2e9-136">パッケージで使用される複数のコンポーネントは、列を同じ名前で公開する場合があります。</span><span class="sxs-lookup"><span data-stu-id="bf2e9-136">Multiple components used in a package can expose columns with the same name.</span></span> <span data-ttu-id="bf2e9-137">これらの列を式で使用する場合、列を明確に識別しなければ、式は正常に解析されません。</span><span class="sxs-lookup"><span data-stu-id="bf2e9-137">If these columns are used in expressions, they must be disambiguated before the expressions can be parsed successfully.</span></span> <span data-ttu-id="bf2e9-138">式エバリュエーターでは、元の列を識別するためのドット付き表記がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="bf2e9-138">The expression evaluator supports the dotted notation for identifying the source of the column.</span></span> <span data-ttu-id="bf2e9-139">たとえば、 **Age** という名前の 2 つの列が **FlatFileSource.Age** と **OLEDBSource.Age**になり、これらの列がそれぞれ FlatFileSource と OLEDBSource に含まれていることを表します。</span><span class="sxs-lookup"><span data-stu-id="bf2e9-139">For example, two columns named **Age** become **FlatFileSource.Age** and **OLEDBSource.Age**, which indicates that their sources are FlatFileSource or OLEDBSource.</span></span> <span data-ttu-id="bf2e9-140">パーサーでは、完全修飾名が 1 つの列名として扱われます。</span><span class="sxs-lookup"><span data-stu-id="bf2e9-140">The parser treats the fully qualified name as a single column name.</span></span>  
  
 <span data-ttu-id="bf2e9-141">基となるコンポーネント名や列名は、個別に修飾されます。</span><span class="sxs-lookup"><span data-stu-id="bf2e9-141">Source component names and column names are qualified separately.</span></span> <span data-ttu-id="bf2e9-142">次の例では、ドット付き表記を使用した角かっこの有効な使用例を示します。</span><span class="sxs-lookup"><span data-stu-id="bf2e9-142">The following examples show valid use of brackets in a dotted notation:</span></span>  
  
-   <span data-ttu-id="bf2e9-143">基となるコンポーネント名にスペースが含まれる場合。</span><span class="sxs-lookup"><span data-stu-id="bf2e9-143">The source component name includes spaces.</span></span>  
  
    ```  
    [MySo urce].Age  
    ```  
  
-   <span data-ttu-id="bf2e9-144">列名の最初の文字が、有効でない場合。</span><span class="sxs-lookup"><span data-stu-id="bf2e9-144">The first character in the column name is not valid.</span></span>  
  
    ```  
    MySource.[#Age]  
    ```  
  
-   <span data-ttu-id="bf2e9-145">基となるコンポーネント名と列名に、無効な文字が含まれる場合。</span><span class="sxs-lookup"><span data-stu-id="bf2e9-145">The source component and the column names contain invalid characters.</span></span>  
  
    ```  
    [MySource?].[#Age]  
    ```  
  
> [!IMPORTANT]  
>  <span data-ttu-id="bf2e9-146">ドット付き表記の両方の要素が 1 組の角かっこで囲まれている場合、式エバリュエーターは、その組を、元の列の組み合わせとしてではなく、単一の識別子として解釈します。</span><span class="sxs-lookup"><span data-stu-id="bf2e9-146">If both elements in dotted notation are enclosed in one pair of brackets, the expression evaluator interprets the pair as a single identifier, not a source-column combination.</span></span>  
  
## <a name="variables-in-expressions"></a><span data-ttu-id="bf2e9-147">式内部の変数</span><span class="sxs-lookup"><span data-stu-id="bf2e9-147">Variables in Expressions</span></span>  
 <span data-ttu-id="bf2e9-148">変数が式の内部で参照される場合、変数には \@ プレフィックスを含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="bf2e9-148">Variables, when referenced in expressions, must include the \@ prefix.</span></span> <span data-ttu-id="bf2e9-149">たとえば、**Counter** 変数を参照する場合、\@Counter を使用します。</span><span class="sxs-lookup"><span data-stu-id="bf2e9-149">For example, the **Counter** variable is referenced by using \@Counter.</span></span> <span data-ttu-id="bf2e9-150">\@ 文字は、変数名の一部ではなく、式の評価において変数を識別するためのものにすぎません。</span><span class="sxs-lookup"><span data-stu-id="bf2e9-150">The \@ character is not part of the variable name; it only identifies the variable to the expression evaluator.</span></span> <span data-ttu-id="bf2e9-151">[!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーで用意されているダイアログ ボックスを使用して式を構築する場合、\@ 文字が自動的に変数名に追加されます。</span><span class="sxs-lookup"><span data-stu-id="bf2e9-151">If you build expressions by using the dialog boxes that [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer provides, the \@ character is automatically added to the variable name.</span></span> <span data-ttu-id="bf2e9-152">\@ 文字と変数名の間にスペースが含まれる場合は、無効になります。</span><span class="sxs-lookup"><span data-stu-id="bf2e9-152">It is not valid to include spaces between the \@ character and the variable name.</span></span>  
  
 <span data-ttu-id="bf2e9-153">変数名は、他の標準識別子の規則と同じく、次の規則に従います。</span><span class="sxs-lookup"><span data-stu-id="bf2e9-153">Variable names follow the same rules as those for other regular identifiers:</span></span>  
  
-   <span data-ttu-id="bf2e9-154">名前の最初の文字は、Unicode Standard 2.0 で定義されている文字か、アンダースコア (_) である必要があります。</span><span class="sxs-lookup"><span data-stu-id="bf2e9-154">The first character of the name must be a letter as defined by the Unicode Standard 2.0, or an underscore (_).</span></span>  
  
-   <span data-ttu-id="bf2e9-155">2 番目以降の文字では、Unicode Standard 2.0 に定義されている文字または数字と、アンダースコア (_)、\@、$、および # 文字を使用できます。</span><span class="sxs-lookup"><span data-stu-id="bf2e9-155">Subsequent characters can be letters or numbers as defined in the Unicode Standard 2.0, the underscore (_), \@, $, and # characters.</span></span>  
  
 <span data-ttu-id="bf2e9-156">上記の一覧に表示されていない文字が変数名に含まれる場合、変数を角かっこで囲む必要があります。</span><span class="sxs-lookup"><span data-stu-id="bf2e9-156">If a variable name contains characters other than those listed, the variable must be enclosed in brackets.</span></span> <span data-ttu-id="bf2e9-157">たとえば、スペースが含まれる変数名は角かっこで囲みます。</span><span class="sxs-lookup"><span data-stu-id="bf2e9-157">For example, variable names with spaces must be enclosed in brackets.</span></span> <span data-ttu-id="bf2e9-158">左角かっこは、\@ 文字の後ろに付けます。</span><span class="sxs-lookup"><span data-stu-id="bf2e9-158">The opening bracket follows the \@ character.</span></span> <span data-ttu-id="bf2e9-159">たとえば、**My Name** 変数は、\@[My Name] として参照されます。</span><span class="sxs-lookup"><span data-stu-id="bf2e9-159">For example, the **My Name** variable is referenced as \@[My Name].</span></span> <span data-ttu-id="bf2e9-160">変数名と角かっこの間にスペースが含まれる場合は、無効になります。</span><span class="sxs-lookup"><span data-stu-id="bf2e9-160">It is not valid to include spaces between the variable name and the brackets.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="bf2e9-161">ユーザー定義変数およびシステム変数の名前では、大文字と小文字が区別されます。</span><span class="sxs-lookup"><span data-stu-id="bf2e9-161">The names of user-defined and system variables are case-sensitive.</span></span>  
  
## <a name="unique-variable-names"></a><span data-ttu-id="bf2e9-162">一意の変数名</span><span class="sxs-lookup"><span data-stu-id="bf2e9-162">Unique Variable Names</span></span>  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] <span data-ttu-id="bf2e9-163">ではカスタム変数がサポートされ、さらにシステム変数のセットが用意されています。</span><span class="sxs-lookup"><span data-stu-id="bf2e9-163">supports custom variables and provides a set of system variables.</span></span> <span data-ttu-id="bf2e9-164">既定では、カスタム変数は **User** 名前空間に属し、システム変数は **System** 名前空間に属します。</span><span class="sxs-lookup"><span data-stu-id="bf2e9-164">By default, custom variables belong to the **User** namespace, and system variables belong to the **System** namespace.</span></span> <span data-ttu-id="bf2e9-165">カスタム変数用に別の名前空間を作成し、名前空間の名前をアプリケーションのニーズに合わせて更新できます。</span><span class="sxs-lookup"><span data-stu-id="bf2e9-165">You can create additional namespaces for custom variables and update the namespace names to suit the needs of your application.</span></span> <span data-ttu-id="bf2e9-166">式ビルダーでは、すべての名前空間にあるスコープ内の変数が一覧表示されます。</span><span class="sxs-lookup"><span data-stu-id="bf2e9-166">The expression builder lists in-scope variables in all namespaces.</span></span>  
  
 <span data-ttu-id="bf2e9-167">すべての変数はスコープを持ち、名前空間に属します。</span><span class="sxs-lookup"><span data-stu-id="bf2e9-167">All variables have scope and belong to a namespace.</span></span> <span data-ttu-id="bf2e9-168">変数は、パッケージ スコープまたは、パッケージ内のコンテナーあるいはタスクのスコープを持ちます。</span><span class="sxs-lookup"><span data-stu-id="bf2e9-168">A variable has package scope or the scope of a container or task in the package.</span></span> <span data-ttu-id="bf2e9-169">[!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーの式ビルダーでは、スコープ内の変数のみが一覧表示されます。</span><span class="sxs-lookup"><span data-stu-id="bf2e9-169">The expression builder in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer lists only the in-scope variables.</span></span> <span data-ttu-id="bf2e9-170">詳細については、「[Integration Services &#40;SSIS&#41; の変数](../integration-services-ssis-variables.md)」と「[パッケージで変数を使用する](../use-variables-in-packages.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="bf2e9-170">For more information, see [Integration Services &#40;SSIS&#41; Variables](../integration-services-ssis-variables.md) and [Use Variables in Packages](../use-variables-in-packages.md).</span></span>  
  
 <span data-ttu-id="bf2e9-171">式で使用される変数名は、式エバリュエーターが式を正しく評価できるよう、一意である必要があります。</span><span class="sxs-lookup"><span data-stu-id="bf2e9-171">Variables used in expressions must have unique names for the expression evaluator to evaluate the expression correctly.</span></span> <span data-ttu-id="bf2e9-172">パッケージで複数の変数を同じ名前で使用する場合、その変数は、それぞれ別の名前空間に属する必要があります。</span><span class="sxs-lookup"><span data-stu-id="bf2e9-172">If a package uses multiple variables with the same name, their namespaces must be different.</span></span> [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] <span data-ttu-id="bf2e9-173">では、2 つのコロン (::) から成る、名前空間を解決する演算子が用意され、変数は名前空間で修飾されます。</span><span class="sxs-lookup"><span data-stu-id="bf2e9-173">provides a namespace resolution operator, consisting of two colons (::), for qualifying a variable with its namespace.</span></span> <span data-ttu-id="bf2e9-174">たとえば、次の式では、 **Count**という名前の 2 つの変数が使用されています。変数の 1 つは **User** 名前空間、もう 1 つの変数は **MyNamespace** 名前空間に属します。</span><span class="sxs-lookup"><span data-stu-id="bf2e9-174">For example, the following expression uses two variables named **Count**; one belongs to the **User** namespace and one to the **MyNamespace** namespace.</span></span>  
  
```  
@[User::Count] > @[MyNamespace::Count]  
```  
  
> [!IMPORTANT]  
>  <span data-ttu-id="bf2e9-175">名前空間の組み合わせおよび修飾された変数名は、式エバリュエーターが変数を認識できるよう、角かっこで囲む必要があります。</span><span class="sxs-lookup"><span data-stu-id="bf2e9-175">You must enclose the combination of namespace and qualified variable name in brackets for the expression evaluator to recognize the variable.</span></span>  
  
 <span data-ttu-id="bf2e9-176">**User**名前空間の**count**の値が10で、 **MyNamespace**の**count**の値が2の場合、式 `true` エバリュエーターが2つの異なる変数を認識するため、式はに評価されます。</span><span class="sxs-lookup"><span data-stu-id="bf2e9-176">If the value of **Count** in the **User** namespace is 10 and the value of **Count** in **MyNamespace** is 2, the expression evaluates to `true` because the expression evaluator recognizes two different variables.</span></span>  
  
 <span data-ttu-id="bf2e9-177">変数名が一意でない場合でもエラーは発生せず、</span><span class="sxs-lookup"><span data-stu-id="bf2e9-177">If variable names are not unique, no error occurs.</span></span> <span data-ttu-id="bf2e9-178">式エバリュエーターは、変数のインスタンスを 1 つのみ使用して式を評価し、間違った結果を返します。</span><span class="sxs-lookup"><span data-stu-id="bf2e9-178">Instead, the expression evaluator uses only one instance of the variable to evaluate the expression and returns an incorrect result.</span></span> <span data-ttu-id="bf2e9-179">たとえば、次の式は、2つの個別の**カウント**変数の値 (10 と 2) を比較するためのものですが、式エバリュエーターでは `false` **count**変数の同じインスタンスが2回使用されるため、式はと評価されます。</span><span class="sxs-lookup"><span data-stu-id="bf2e9-179">For example, the following expression was intended to compare the values (10 and 2) for two separate **Count** variables but the expression evaluates to `false` because the expression evaluator uses the same instance of the **Count** variable two times.</span></span>  
  
```  
@Count > @Count  
```  
  
## <a name="related-content"></a><span data-ttu-id="bf2e9-180">関連コンテンツ</span><span class="sxs-lookup"><span data-stu-id="bf2e9-180">Related Content</span></span>  
 <span data-ttu-id="bf2e9-181">pragmaticworks.com の技術記事「 [SSIS 式チート シート](https://pragmaticworks.com/Resources/Cheat-Sheets/SSIS-Expression-Cheat-Sheet)」</span><span class="sxs-lookup"><span data-stu-id="bf2e9-181">Technical article, [SSIS Expression Cheat Sheet](https://pragmaticworks.com/Resources/Cheat-Sheets/SSIS-Expression-Cheat-Sheet), on pragmaticworks.com</span></span>  
  
  
