---
title: ユーザー、ロール、およびログインの管理 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- logins [SMO]
- roles [SMO]
- users [SMO]
ms.assetid: 74e411fa-74ed-49ec-ab58-68c250f2280e
author: stevestein
ms.author: sstein
ms.openlocfilehash: bb53e7b4a5748e46c7cb147e1cda50652d8b8805
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643212"
---
# <a name="managing-users-roles-and-logins"></a><span data-ttu-id="90288-102">ユーザー、ロール、およびログインの管理</span><span class="sxs-lookup"><span data-stu-id="90288-102">Managing Users, Roles, and Logins</span></span>
  <span data-ttu-id="90288-103">SMO では、<xref:Microsoft.SqlServer.Management.Smo.Login> オブジェクトでログインが表現されます。</span><span class="sxs-lookup"><span data-stu-id="90288-103">In SMO, logins are represented by the <xref:Microsoft.SqlServer.Management.Smo.Login> object.</span></span> <span data-ttu-id="90288-104">ログオンが [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]に存在する場合、サーバー ロールに追加することができます。</span><span class="sxs-lookup"><span data-stu-id="90288-104">When the logon exists in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], it can be added to a server role.</span></span> <span data-ttu-id="90288-105">サーバー ロールは、<xref:Microsoft.SqlServer.Management.Smo.ServerRole> オブジェクトで表現されます。</span><span class="sxs-lookup"><span data-stu-id="90288-105">The server role is represented by the <xref:Microsoft.SqlServer.Management.Smo.ServerRole> object.</span></span> <span data-ttu-id="90288-106">データベース ロールは <xref:Microsoft.SqlServer.Management.Smo.DatabaseRole> オブジェクトで表現され、アプリケーション ロールは <xref:Microsoft.SqlServer.Management.Smo.ApplicationRole> オブジェクトで表現されます。</span><span class="sxs-lookup"><span data-stu-id="90288-106">The database role is represented by the <xref:Microsoft.SqlServer.Management.Smo.DatabaseRole> object and the application role is represented by the <xref:Microsoft.SqlServer.Management.Smo.ApplicationRole> object.</span></span>  
  
 <span data-ttu-id="90288-107">サーバー レベルに関連付けられた権限は、<xref:Microsoft.SqlServer.Management.Smo.ServerPermission> オブジェクトのプロパティとしてリストされます。</span><span class="sxs-lookup"><span data-stu-id="90288-107">Privileges associated with the server level are listed as properties of the <xref:Microsoft.SqlServer.Management.Smo.ServerPermission> object.</span></span> <span data-ttu-id="90288-108">サーバー レベル権限は、個々のログオン アカウントに対して、許可、拒否、取り消しを行うことができます。</span><span class="sxs-lookup"><span data-stu-id="90288-108">The server level privileges can be granted to, denied to, or revoked from individual logon accounts.</span></span>  
  
 <span data-ttu-id="90288-109">各 <xref:Microsoft.SqlServer.Management.Smo.Database> オブジェクトには、データベース内のすべてのユーザーを指定する <xref:Microsoft.SqlServer.Management.Smo.UserCollection> オブジェクトがあります。</span><span class="sxs-lookup"><span data-stu-id="90288-109">Every <xref:Microsoft.SqlServer.Management.Smo.Database> object has a <xref:Microsoft.SqlServer.Management.Smo.UserCollection> object that specifies all users in the database.</span></span> <span data-ttu-id="90288-110">各ユーザーはログオンに関連付けられています。</span><span class="sxs-lookup"><span data-stu-id="90288-110">Each user is associated with a logon.</span></span> <span data-ttu-id="90288-111">1 つのログオンを 2 つ以上のデータベース内のユーザーに関連付けることもできます。</span><span class="sxs-lookup"><span data-stu-id="90288-111">One logon can be associated with users in more than one database.</span></span> <span data-ttu-id="90288-112">ログオンに関連付けられた各データベース内のすべてのユーザーをリストするには、<xref:Microsoft.SqlServer.Management.Smo.Login> オブジェクトの <xref:Microsoft.SqlServer.Management.Smo.Login.EnumDatabaseMappings%2A> メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="90288-112">The <xref:Microsoft.SqlServer.Management.Smo.Login> object's <xref:Microsoft.SqlServer.Management.Smo.Login.EnumDatabaseMappings%2A> method can be used to list all users in every database that is associated with the logon.</span></span> <span data-ttu-id="90288-113">または、<xref:Microsoft.SqlServer.Management.Smo.User> オブジェクトの <xref:Microsoft.SqlServer.Management.Smo.Login> プロパティで、ユーザーに関連付けられたログオンを指定します。</span><span class="sxs-lookup"><span data-stu-id="90288-113">Alternatively, the <xref:Microsoft.SqlServer.Management.Smo.User> object's <xref:Microsoft.SqlServer.Management.Smo.Login> property specifies the logon that is associated with the user.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="90288-114">データベースには、ユーザーに対して特定のタスクの実行を許可するための、データベース レベル権限のセットを指定するロールもあります。</span><span class="sxs-lookup"><span data-stu-id="90288-114">databases also have roles that specify a set of database level privileges that let a user perform specific tasks.</span></span> <span data-ttu-id="90288-115">サーバー ロールと異なり、データベース ロールは固定されていません。</span><span class="sxs-lookup"><span data-stu-id="90288-115">Unlike server roles, database roles are not fixed.</span></span> <span data-ttu-id="90288-116">データベース ロールは、作成、変更、および削除を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="90288-116">They can be created, modified, and removed.</span></span> <span data-ttu-id="90288-117">権限およびユーザーは、データベースに割り当てて、一括管理することができます。</span><span class="sxs-lookup"><span data-stu-id="90288-117">Privileges and users can be assigned to a database role for bulk administration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="90288-118">例</span><span class="sxs-lookup"><span data-stu-id="90288-118">Example</span></span>  
 <span data-ttu-id="90288-119">次のコード例では、アプリケーションを作成するプログラミング環境、プログラミング テンプレート、およびプログラミング言語を選択する必要があります。</span><span class="sxs-lookup"><span data-stu-id="90288-119">For the following code example, you will have to select the programming environment, programming template and the programming language to create your application.</span></span> <span data-ttu-id="90288-120">詳細については、「 [Visual studio .net での VISUAL BASIC Smo プロジェクトの作成](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md)」および「visual [Studio .Net で VISUAL C&#35; Smo プロジェクトを作成](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="90288-120">For more information, see [Create a Visual Basic SMO Project in Visual Studio .NET](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md) and [Create a Visual C&#35; SMO Project in Visual Studio .NET](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).</span></span>  
  
## <a name="enumerating-logins-and-associated-users-in-visual-basic"></a><span data-ttu-id="90288-121">Visual Basic でのログインおよび関連付けられたユーザーの列挙</span><span class="sxs-lookup"><span data-stu-id="90288-121">Enumerating Logins and Associated Users in Visual Basic</span></span>  
 <span data-ttu-id="90288-122">データベース内の各ユーザーは、ログオンに関連付けられています。</span><span class="sxs-lookup"><span data-stu-id="90288-122">Every user in a database is associated with a logon.</span></span> <span data-ttu-id="90288-123">ログオンは 2 つ以上のデータベース内のユーザーに関連付けることもできます。</span><span class="sxs-lookup"><span data-stu-id="90288-123">The logon can be associated with users in more than one database.</span></span> <span data-ttu-id="90288-124">コード例では、<xref:Microsoft.SqlServer.Management.Smo.Login.EnumDatabaseMappings%2A> オブジェクトの <xref:Microsoft.SqlServer.Management.Smo.Login> メソッドを呼び出して、ログオンに関連付けられているすべてのデータベース ユーザーをリストする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="90288-124">The code example shows how to call the <xref:Microsoft.SqlServer.Management.Smo.Login.EnumDatabaseMappings%2A> method of the <xref:Microsoft.SqlServer.Management.Smo.Login> object to list all the database users who are associated with the logon.</span></span> <span data-ttu-id="90288-125">この例では、 [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] データベースのログオンおよびユーザーを作成して、列挙するマッピング情報の存在を確認します。</span><span class="sxs-lookup"><span data-stu-id="90288-125">The example creates a logon and user in the [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] database to make sure there is mapping information to enumerate.</span></span>  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBLogins1](SMO How to#SMO_VBLogins1)]  -->  
  
## <a name="enumerating-logins-and-associated-users-in-visual-c"></a><span data-ttu-id="90288-126">Visual C# でのログインおよび関連付けられたユーザーの列挙</span><span class="sxs-lookup"><span data-stu-id="90288-126">Enumerating Logins and Associated Users in Visual C#</span></span>  
 <span data-ttu-id="90288-127">データベース内の各ユーザーは、ログオンに関連付けられています。</span><span class="sxs-lookup"><span data-stu-id="90288-127">Every user in a database is associated with a logon.</span></span> <span data-ttu-id="90288-128">ログオンは 2 つ以上のデータベース内のユーザーに関連付けることもできます。</span><span class="sxs-lookup"><span data-stu-id="90288-128">The logon can be associated with users in more than one database.</span></span> <span data-ttu-id="90288-129">コード例では、<xref:Microsoft.SqlServer.Management.Smo.Login.EnumDatabaseMappings%2A> オブジェクトの <xref:Microsoft.SqlServer.Management.Smo.Login> メソッドを呼び出して、ログオンに関連付けられているすべてのデータベース ユーザーをリストする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="90288-129">The code example shows how to call the <xref:Microsoft.SqlServer.Management.Smo.Login.EnumDatabaseMappings%2A> method of the <xref:Microsoft.SqlServer.Management.Smo.Login> object to list all the database users who are associated with the logon.</span></span> <span data-ttu-id="90288-130">この例では、 [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] データベースのログオンおよびユーザーを作成して、列挙するマッピング情報の存在を確認します。</span><span class="sxs-lookup"><span data-stu-id="90288-130">The example creates a logon and user in the [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] database to make sure there is mapping information to enumerate.</span></span>  
  
```csharp
{   
Server srv = new Server();   
//Iterate through each database and display.   
  
foreach ( Database db in srv.Databases) {   
   Console.WriteLine("========");   
   Console.WriteLine("Login Mappings for the database: " + db.Name);   
   Console.WriteLine(" ");   
   //Run the EnumLoginMappings method and return details of database user-login mappings to a DataTable object variable.   
   DataTable d;  
   d = db.EnumLoginMappings();   
   //Display the mapping information.   
   foreach (DataRow r in d.Rows) {   
      foreach (DataColumn c in r.Table.Columns) {   
         Console.WriteLine(c.ColumnName + " = " + r[c]);   
      }   
      Console.WriteLine(" ");   
   }   
}   
}  
```  
  
## <a name="enumerating-logins-and-associated-users-in-powershell"></a><span data-ttu-id="90288-131">PowerShell でのログインおよび関連付けられたユーザーの列挙</span><span class="sxs-lookup"><span data-stu-id="90288-131">Enumerating Logins and Associated Users in PowerShell</span></span>  
 <span data-ttu-id="90288-132">データベース内の各ユーザーは、ログオンに関連付けられています。</span><span class="sxs-lookup"><span data-stu-id="90288-132">Every user in a database is associated with a logon.</span></span> <span data-ttu-id="90288-133">ログオンは 2 つ以上のデータベース内のユーザーに関連付けることもできます。</span><span class="sxs-lookup"><span data-stu-id="90288-133">The logon can be associated with users in more than one database.</span></span> <span data-ttu-id="90288-134">コード例では、<xref:Microsoft.SqlServer.Management.Smo.Login.EnumDatabaseMappings%2A> オブジェクトの <xref:Microsoft.SqlServer.Management.Smo.Login> メソッドを呼び出して、ログオンに関連付けられているすべてのデータベース ユーザーをリストする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="90288-134">The code example shows how to call the <xref:Microsoft.SqlServer.Management.Smo.Login.EnumDatabaseMappings%2A> method of the <xref:Microsoft.SqlServer.Management.Smo.Login> object to list all the database users who are associated with the logon.</span></span> <span data-ttu-id="90288-135">この例では、 [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] データベースのログオンおよびユーザーを作成して、列挙するマッピング情報の存在を確認します。</span><span class="sxs-lookup"><span data-stu-id="90288-135">The example creates a logon and user in the [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] database to make sure there is mapping information to enumerate.</span></span>  
  
```powershell
# Set the path context to the local, default instance of SQL Server.  
CD \sql\localhost\Default\Databases  
  
#Iterate through all databases  
 foreach ($db in Get-ChildItem)  
 {  
 "====="  
 "Login Mappings for the database: "+ $db.Name  
  
 #get the datatable containing the mapping from the smo database object  
 $dt = $db.EnumLoginMappings()  
  
 #display the results  
 foreach($row in $dt.Rows)  
     {  
        foreach($col in $row.Table.Columns)  
      {  
        $col.ColumnName + "=" + $row[$col]  
       }
     }  
 }  
```  
  
## <a name="managing-roles-and-users"></a><span data-ttu-id="90288-136">ロールとユーザーの管理</span><span class="sxs-lookup"><span data-stu-id="90288-136">Managing Roles and Users</span></span>  
 <span data-ttu-id="90288-137">このサンプルでは、ロールおよびユーザーの管理方法を示します。</span><span class="sxs-lookup"><span data-stu-id="90288-137">This sample demonstrates how to how to manage roles and users.</span></span> <span data-ttu-id="90288-138">最初のサンプルでは C# を使用し、2 番目のサンプルでは Visual Basic を使用しています。</span><span class="sxs-lookup"><span data-stu-id="90288-138">The first sample uses C#, the second Visual Basic.</span></span> <span data-ttu-id="90288-139">これらのサンプルでは、次に示すアセンブリへの参照が必要です。</span><span class="sxs-lookup"><span data-stu-id="90288-139">These samples need to reference the following assemblies:</span></span>  
  
-   <span data-ttu-id="90288-140">Microsoft.SqlServer.Smo.dll</span><span class="sxs-lookup"><span data-stu-id="90288-140">Microsoft.SqlServer.Smo.dll</span></span>  
  
-   <span data-ttu-id="90288-141">Microsoft.SqlServer.Management.Sdk.Sfc.dll</span><span class="sxs-lookup"><span data-stu-id="90288-141">Microsoft.SqlServer.Management.Sdk.Sfc.dll</span></span>  
  
-   <span data-ttu-id="90288-142">Microsoft.SqlServer.ConnectionInfo.dll</span><span class="sxs-lookup"><span data-stu-id="90288-142">Microsoft.SqlServer.ConnectionInfo.dll</span></span>  
  
-   <span data-ttu-id="90288-143">Microsoft.SqlServer.SqlEnum.dll</span><span class="sxs-lookup"><span data-stu-id="90288-143">Microsoft.SqlServer.SqlEnum.dll</span></span>  
  
```csharp
using Microsoft.SqlServer.Management.Smo;  
using System;  
  
public class A {  
   public static void Main() {  
      Server svr = new Server();  
      Database db = new Database(svr, "TESTDB");  
      db.Create();  
  
      // Creating Logins  
      Login login = new Login(svr, "Login1");  
      login.LoginType = LoginType.SqlLogin;  
      login.Create("password@1");  
  
      Login login2 = new Login(svr, "Login2");  
      login2.LoginType = LoginType.SqlLogin;  
      login2.Create("password@1");  
  
      // Creating Users in the database for the logins created  
      User user1 = new User(db, "User1");  
      user1.Login = "Login1";  
      user1.Create();  
  
      User user2 = new User(db, "User2");  
      user2.Login = "Login2";  
      user2.Create();  
  
      // Creating database permission Sets  
      DatabasePermissionSet dbPermSet = new DatabasePermissionSet(DatabasePermission.AlterAnySchema);  
      dbPermSet.Add(DatabasePermission.AlterAnyUser);  
  
      DatabasePermissionSet dbPermSet2 = new DatabasePermissionSet(DatabasePermission.CreateType);  
      dbPermSet2.Add(DatabasePermission.CreateSchema);  
      dbPermSet2.Add(DatabasePermission.CreateTable);  
  
      // Creating Database roles  
      DatabaseRole role1 = new DatabaseRole(db, "Role1");  
      role1.Create();  
  
      DatabaseRole role2 = new DatabaseRole(db, "Role2");  
      role2.Create();  
  
      // Granting Database Permission Sets to Roles  
      db.Grant(dbPermSet, role1.Name);  
      db.Grant(dbPermSet2, role2.Name);  
  
      // Adding members (Users / Roles) to Role  
      role1.AddMember("User1");  
  
      role2.AddMember("User2");  
  
      // Role1 becomes a member of Role2  
      role2.AddMember("Role1");  
  
      // Enumerating through explicit permissions granted to Role1  
      // enumerates all database permissions for the Grantee  
      DatabasePermissionInfo[] dbPermsRole1 = db.EnumDatabasePermissions("Role1");     
      foreach (DatabasePermissionInfo dbp in dbPermsRole1) {  
         Console.WriteLine(dbp.Grantee + " has " + dbp.PermissionType.ToString() + " permission.");  
      }  
      Console.WriteLine(" ");  
   }  
}  
```  
  
 <span data-ttu-id="90288-144">Visual Basic バージョンを次に示します。</span><span class="sxs-lookup"><span data-stu-id="90288-144">This is the Visual Basic version:</span></span>  
  
```vb
Imports Microsoft.SqlServer.Management.Smo  
  
Public Class A  
   Public Shared Sub Main()  
      Dim svr As New Server()  
      Dim db As New Database(svr, "TESTDB")  
      db.Create()  
  
      ' Creating Logins  
      Dim login As New Login(svr, "Login1")  
      login.LoginType = LoginType.SqlLogin  
      login.Create("password@1")  
  
      Dim login2 As New Login(svr, "Login2")  
      login2.LoginType = LoginType.SqlLogin  
      login2.Create("password@1")  
  
      ' Creating Users in the database for the logins created  
      Dim user1 As New User(db, "User1")  
      user1.Login = "Login1"  
      user1.Create()  
  
      Dim user2 As New User(db, "User2")  
      user2.Login = "Login2"  
      user2.Create()  
  
      ' Creating database permission Sets  
      Dim dbPermSet As New DatabasePermissionSet(DatabasePermission.AlterAnySchema)  
      dbPermSet.Add(DatabasePermission.AlterAnyUser)  
  
      Dim dbPermSet2 As New DatabasePermissionSet(DatabasePermission.CreateType)  
      dbPermSet2.Add(DatabasePermission.CreateSchema)  
      dbPermSet2.Add(DatabasePermission.CreateTable)  
  
      ' Creating Database roles  
      Dim role1 As New DatabaseRole(db, "Role1")  
      role1.Create()  
  
      Dim role2 As New DatabaseRole(db, "Role2")  
      role2.Create()  
  
      ' Granting Database Permission Sets to Roles  
      db.Grant(dbPermSet, role1.Name)  
      db.Grant(dbPermSet2, role2.Name)  
  
      ' Adding members (Users / Roles) to Role  
      role1.AddMember("User1")  
  
      role2.AddMember("User2")  
  
      ' Role1 becomes a member of Role2  
      role2.AddMember("Role1")  
  
      ' Enumerating through explicit permissions granted to Role1  
      ' enumerates all database permissions for the Grantee  
      Dim dbPermsRole1 As DatabasePermissionInfo() = db.EnumDatabasePermissions("Role1")  
      For Each dbp As DatabasePermissionInfo In dbPermsRole1  
         Console.WriteLine(dbp.Grantee + " has " & dbp.PermissionType.ToString() & " permission.")  
      Next  
      Console.WriteLine(" ")  
   End Sub  
End Class  
```  
