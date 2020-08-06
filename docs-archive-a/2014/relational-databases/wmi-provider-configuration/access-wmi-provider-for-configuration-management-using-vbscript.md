---
title: VBScript を使用して SQL Server サービスの詳細プロパティを変更する |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
dev_langs:
- VB
helpviewer_keywords:
- VBScript [WMI]
- modifying SQL Server Service properties
- WMI Provider for Configuration Management, VBScript
ms.assetid: f3c5d981-eaa3-4d34-9b91-37e42636aa81
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 2cf722b00a31723b77624c33fef81a82ff0cb926
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645419"
---
# <a name="modify-sql-server-service-advanced-properties-using-vbscript"></a><span data-ttu-id="118da-102">VBScript を使用して SQL Server サービスの詳細プロパティを変更する</span><span class="sxs-lookup"><span data-stu-id="118da-102">Modify SQL Server Service Advanced Properties using VBScript</span></span>
  <span data-ttu-id="118da-103">このセクションで [!INCLUDE[msCoName](../../includes/msconame-md.md)] は、コンピューター上で実行されているのインストール済みインスタンスのバージョンを一覧表示する VBScript プログラムを作成する方法について説明し [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="118da-103">This section describes how to create a VBScript program that lists the version of installed instances of [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that are running on a computer.</span></span>  
  
 <span data-ttu-id="118da-104">コード例では、コンピューター上で実行されている [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスおよびそのバージョンをリストします。</span><span class="sxs-lookup"><span data-stu-id="118da-104">The code example lists the instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] running on the computer and its version.</span></span>  
  
### <a name="listing-name-and-version-of-installed-instances-of-sql-server"></a><span data-ttu-id="118da-105">SQL Server のインストール済みインスタンスの名前およびバージョンのリスト表示</span><span class="sxs-lookup"><span data-stu-id="118da-105">Listing name and version of installed instances of SQL Server</span></span>  
  
1.  <span data-ttu-id="118da-106">[!INCLUDE[msCoName](../../includes/msconame-md.md)] のメモ帳など、テキスト エディターで新しいドキュメントを開きます。</span><span class="sxs-lookup"><span data-stu-id="118da-106">Open a new document in a text editor, such as [!INCLUDE[msCoName](../../includes/msconame-md.md)] Notepad.</span></span> <span data-ttu-id="118da-107">この手順の後に示すコードをコピーし、.vbs 拡張子を付けてファイルを保存します。</span><span class="sxs-lookup"><span data-stu-id="118da-107">Copy the code that follows this procedure and save the file with a .vbs extension.</span></span> <span data-ttu-id="118da-108">この例の名前を test.vbs とします。</span><span class="sxs-lookup"><span data-stu-id="118da-108">This example is called test.vbs.</span></span>  
  
2.  <span data-ttu-id="118da-109">VBScript の `GetObject` 関数を使用して、コンピューター管理用の WMI プロバイダーのインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="118da-109">Connect to an instance of the WMI Provider for Computer Management with the VBScript `GetObject` function.</span></span> <span data-ttu-id="118da-110">この例では、mpc という名前のリモート コンピューターに接続しますが、コンピューター名は省略してローカル コンピューター (winmgmts:root\Microsoft\SqlServer\ComputerManagement) に接続してください。</span><span class="sxs-lookup"><span data-stu-id="118da-110">This example connects to a remote computer named mpc, but omit the computer name to connect to the local computer: winmgmts:root\Microsoft\SqlServer\ComputerManagement.</span></span> <span data-ttu-id="118da-111">`GetObject` 関数の詳細については、VBScript リファレンスを参照してください。</span><span class="sxs-lookup"><span data-stu-id="118da-111">For more information about the `GetObject` function, see the VBScript reference.</span></span>  
  
3.  <span data-ttu-id="118da-112">`InstancesOf` メソッドを使用して、サービスのリストを列挙します。</span><span class="sxs-lookup"><span data-stu-id="118da-112">Use the `InstancesOf` method to enumerate a list of the services.</span></span> <span data-ttu-id="118da-113">サービスは、`ExecQuery` メソッドの代わりに、簡単な WQL クエリと `InstancesOf` メソッドを使用して列挙することもできます。</span><span class="sxs-lookup"><span data-stu-id="118da-113">The services can also be enumerated by using a simple WQL query and an `ExecQuery` method instead of the `InstancesOf` method.</span></span>  
  
4.  <span data-ttu-id="118da-114">`ExecQuery` メソッドおよび WQL クエリを使用して、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインストール済みインスタンスの名前およびバージョンを取得します。</span><span class="sxs-lookup"><span data-stu-id="118da-114">Use the `ExecQuery` method and a WQL query to retrieve the name and version of the installed instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
5.  <span data-ttu-id="118da-115">ファイルを保存します。</span><span class="sxs-lookup"><span data-stu-id="118da-115">Save the file.</span></span>  
  
6.  <span data-ttu-id="118da-116">コマンドプロンプトで「」と入力して、スクリプトを実行し `cscript test.vbs` ます。</span><span class="sxs-lookup"><span data-stu-id="118da-116">Run the script by typing `cscript test.vbs` at the command prompt.</span></span>  
  
## <a name="example"></a><span data-ttu-id="118da-117">例</span><span class="sxs-lookup"><span data-stu-id="118da-117">Example</span></span>  
  
```  
set wmi = GetObject("WINMGMTS:\\.\root\Microsoft\SqlServer\ComputerManagement12")  
for each prop in wmi.ExecQuery("select * from SqlServiceAdvancedProperty where SQLServiceType = 1 AND PropertyName = 'VERSION'")  
WScript.Echo prop.ServiceName & " " & prop.PropertyName & ": " & prop.PropertyStrValue  
next  
```  
  
  
