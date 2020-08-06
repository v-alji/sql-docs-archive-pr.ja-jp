---
title: Transact-SQL スニペットの追加
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 901c7995-8eb5-4d12-8bb0-de0a922b48f8
author: rothja
ms.author: jroth
ms.openlocfilehash: 5b5886f8f36ae3753fcb7c89dd3aeff9c69eeba5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634925"
---
# <a name="add-transact-sql-snippets"></a><span data-ttu-id="7fa96-102">Transact-SQL スニペットの追加</span><span class="sxs-lookup"><span data-stu-id="7fa96-102">Add Transact-SQL Snippets</span></span>
  <span data-ttu-id="7fa96-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]には、定義済みの Transact-SQL コード スニペット一式が同梱されていますが、それ以外にも、独自のスニペットを追加することができます。</span><span class="sxs-lookup"><span data-stu-id="7fa96-103">You can add your own Transact-SQL code snippets to the set of pre-defined snippets included in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="creating-a-transact-sql-snippet-file"></a><span data-ttu-id="7fa96-104">Transact-SQL スニペット ファイルの作成</span><span class="sxs-lookup"><span data-stu-id="7fa96-104">Creating a Transact-SQL Snippet File</span></span>  
 <span data-ttu-id="7fa96-105">[!INCLUDE[tsql](../../includes/tsql-md.md)] コード スニペットを作成するには、まず、目的のコード スニペットのテキストを含んだ XML ファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="7fa96-105">The first part of creating a [!INCLUDE[tsql](../../includes/tsql-md.md)] code snippet is to create an XML file with the text of your code snippet.</span></span> <span data-ttu-id="7fa96-106">このファイルは、拡張子を .snippet とし、 [コード スニペット スキーマ](https://go.microsoft.com/fwlink/?LinkId=207504)の要件を満たしている必要があります。</span><span class="sxs-lookup"><span data-stu-id="7fa96-106">The file must have a .snippet file extension, and meet the requirements of the [Code Snippets Schema](https://go.microsoft.com/fwlink/?LinkId=207504).</span></span> <span data-ttu-id="7fa96-107">スニペットの言語は SQL に設定します。</span><span class="sxs-lookup"><span data-stu-id="7fa96-107">Set the snippet language to SQL.</span></span>  
  
 <span data-ttu-id="7fa96-108">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に付属する定義済みのスニペットが参考になります。</span><span class="sxs-lookup"><span data-stu-id="7fa96-108">You can use the pre-defined snippets that ship with [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] as examples.</span></span> <span data-ttu-id="7fa96-109">定義済みのスニペットを探すには、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]を開いて **[ツール]** メニューを選択し、 **[コード スニペット マネージャー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7fa96-109">To find the pre-defined snippets, open [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], select the **Tools** menu, and click **Code Snippet Manager**.</span></span> <span data-ttu-id="7fa96-110">**[言語]** ボックスの一覧の **[SQL]** をクリックすると、 [!INCLUDE[tsql](../../includes/tsql-md.md)] スニペットのパスが **[場所]** ボックスに表示されます。</span><span class="sxs-lookup"><span data-stu-id="7fa96-110">Select **SQL** in the **Language** list box, the path to the [!INCLUDE[tsql](../../includes/tsql-md.md)] snippets is displayed in the **Location** box.</span></span>  
  
## <a name="registering-the-code-snippet"></a><span data-ttu-id="7fa96-111">コード スニペットの登録</span><span class="sxs-lookup"><span data-stu-id="7fa96-111">Registering the Code Snippet</span></span>  
 <span data-ttu-id="7fa96-112">スニペット ファイルを作成したら、コード スニペット マネージャーを使用して、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]にスニペットを登録します。</span><span class="sxs-lookup"><span data-stu-id="7fa96-112">After creating the snippet file, use the Code Snippets Manager to register the snippet with [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="7fa96-113">複数のスニペットを含んだフォルダーを追加するか、個々のスニペットを **[マイ コード スニペット]** フォルダーにインポートすることができます。</span><span class="sxs-lookup"><span data-stu-id="7fa96-113">You can either add a folder containing multiple snippets, or import individual snippets to the **My Code Snippets** folder.</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="7fa96-114">手順</span><span class="sxs-lookup"><span data-stu-id="7fa96-114">Procedures</span></span>  
  
#### <a name="adding-a-snippet-folder"></a><span data-ttu-id="7fa96-115">スニペット フォルダーの追加</span><span class="sxs-lookup"><span data-stu-id="7fa96-115">Adding a Snippet Folder</span></span>  
  
1.  <span data-ttu-id="7fa96-116">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]を開きます。</span><span class="sxs-lookup"><span data-stu-id="7fa96-116">Open [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
2.  <span data-ttu-id="7fa96-117">**[ツール]** メニューを選択し、 **[コード スニペット マネージャー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7fa96-117">Select the **Tools** menu, and click **Code Snippets Manager**.</span></span>  
  
3.  <span data-ttu-id="7fa96-118">**[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7fa96-118">Click the **Add** button.</span></span>  
  
4.  <span data-ttu-id="7fa96-119">コード スニペットがあるフォルダーに移動し、 **[フォルダーの選択]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7fa96-119">Navigate to the folder containing your code snippets, and click the **Select Folder** button.</span></span>  
  
#### <a name="importing-a-snippet"></a><span data-ttu-id="7fa96-120">スニペットのインポート</span><span class="sxs-lookup"><span data-stu-id="7fa96-120">Importing a Snippet</span></span>  
  
1.  <span data-ttu-id="7fa96-121">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]を開きます。</span><span class="sxs-lookup"><span data-stu-id="7fa96-121">Open [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
2.  <span data-ttu-id="7fa96-122">**[ツール]** メニューを選択し、 **[コード スニペット マネージャー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7fa96-122">Select the **Tools** menu, and click **Code Snippets Manager**.</span></span>  
  
3.  <span data-ttu-id="7fa96-123">**[Import]\(インポート\)** ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="7fa96-123">Click the **Import** button.</span></span>  
  
4.  <span data-ttu-id="7fa96-124">スニペットがあるフォルダーに移動し、.snippet ファイルをクリックして、 **[開く]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7fa96-124">Navigate to the folder containing your snippet, click on the .snippet file, and click the **Open** button.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="7fa96-125">例</span><span class="sxs-lookup"><span data-stu-id="7fa96-125">Examples</span></span>  
 <span data-ttu-id="7fa96-126">次の例では、`TRY-CATCH` ブロックの挿入スニペットを作成し、[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] にインポートします。</span><span class="sxs-lookup"><span data-stu-id="7fa96-126">The following example creates a `TRY-CATCH` surround-with snippet and imports it to [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
1.  <span data-ttu-id="7fa96-127">次のコードをメモ帳に貼り付け、TryCatch.snippet というファイル名で保存します。</span><span class="sxs-lookup"><span data-stu-id="7fa96-127">Paste the following code into notepad, then save as a file named TryCatch.snippet.</span></span>  
  
    ```  
    <?xml version="1.0" encoding="utf-8" ?>  
    <CodeSnippets  xmlns="https://schemas.microsoft.com/VisualStudio/2005/CodeSnippet">  
    <_locDefinition xmlns="urn:locstudio">  
        <_locDefault _loc="locNone" />  
        <_locTag _loc="locData">Title</_locTag>  
        <_locTag _loc="locData">Description</_locTag>  
        <_locTag _loc="locData">Author</_locTag>  
        <_locTag _loc="locData">ToolTip</_locTag>  
       <_locTag _loc="locData">Default</_locTag>  
    </_locDefinition>  
    <CodeSnippet Format="1.0.0">  
    <Header>  
    <Title>TryCatch</Title>  
                            <Shortcut></Shortcut>  
    <Description>Example Snippet for Try-Catch.</Description>  
    <Author>SQL Server Books Online Example</Author>  
    <SnippetTypes>  
                                    <SnippetType>SurroundsWith</SnippetType>  
    </SnippetTypes>  
    </Header>  
    <Snippet>  
    <Declarations>  
                                    <Literal>  
                                    <ID>CatchCode</ID>  
                                    <ToolTip>Code to handle the caught error</ToolTip>  
                                    <Default>CatchCode</Default>  
                                    </Literal>  
    </Declarations>  
    <Code Language="SQL"><![CDATA[  
    BEGIN TRY  
  
    $selected$ $end$  
  
    END TRY  
    BEGIN CATCH  
  
    $CatchCode$  
  
    END CATCH;  
    ]]>  
    </Code>  
    </Snippet>  
    </CodeSnippet>  
    </CodeSnippets>  
    ```  
  
2.  <span data-ttu-id="7fa96-128">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]を開きます。</span><span class="sxs-lookup"><span data-stu-id="7fa96-128">Open [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
3.  <span data-ttu-id="7fa96-129">**[ツール]** メニューを選択し、 **[コード スニペット マネージャー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7fa96-129">Select the **Tools** menu, and click **Code Snippets Manager**.</span></span>  
  
4.  <span data-ttu-id="7fa96-130">**[Import]\(インポート\)** ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="7fa96-130">Click the **Import** button.</span></span>  
  
5.  <span data-ttu-id="7fa96-131">TryCatch.snippet があるフォルダーに移動し、TryCatch.snippet ファイルをクリックして、 **[開く]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7fa96-131">Navigate to the folder containing TryCatch.snippet, click on the TryCatch.snippet file, and click the **Open** button.</span></span> <span data-ttu-id="7fa96-132">**[マイ コード スニペット]** フォルダーに既存の TryCatch スニペットがないことが前提になります。</span><span class="sxs-lookup"><span data-stu-id="7fa96-132">You should not have a TryCatch snippet in your **My Code Snippets** folder.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7fa96-133">参照</span><span class="sxs-lookup"><span data-stu-id="7fa96-133">See Also</span></span>  
 [<span data-ttu-id="7fa96-134">ブロックの挿入 Transact-SQL スニペットの挿入</span><span class="sxs-lookup"><span data-stu-id="7fa96-134">Insert Surround-with Transact-SQL snippets</span></span>](insert-surround-with-transact-sql-snippets.md)  
  
  
