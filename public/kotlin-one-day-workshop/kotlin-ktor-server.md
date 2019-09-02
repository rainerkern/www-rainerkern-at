kotlin-ktor-client-server
==============================
Step-1-Setup-Git-Repository
------------------------------
commit 983d901b48c0961ae42d623e1b90fcd88c562b97
Author: rainer <rainer@systemkern.com>
Date:   Wed Aug 28 12:40:01 2019 +0200

    Step 8: Add JSON serialization
    
    Since we do not want to manually write our JSON output, we are going to
    utilise a Kotlin's built in serialization capabilities.


```
diff --git a/build.gradle b/build.gradle
index abb3541..bcafcf7 100644
--- a/build.gradle
+++ b/build.gradle
@@ -6,6 +6,7 @@
  */
 buildscript {
     ext.kotlin_version = "1.3.41"
+    ext.serialization_version = "0.11.0"
     ext.ktor_version = '1.1.4'
     ext.kotlinx_html_version = "0.6.12"
 
@@ -16,11 +17,14 @@ buildscript {
 
     dependencies {
         classpath "org.jetbrains.kotlin:kotlin-gradle-plugin:$kotlin_version"
+        classpath "org.jetbrains.kotlin:kotlin-serialization:$kotlin_version"
     }
 }
 
 apply plugin: 'java'
 apply plugin: 'kotlin'
+apply plugin: 'kotlinx-serialization'
+
 
 // repositories for downloading application dependencies
 repositories {
@@ -30,6 +34,7 @@ repositories {
 
 dependencies {
     compile "org.jetbrains.kotlin:kotlin-stdlib:$kotlin_version"
+    compile "org.jetbrains.kotlinx:kotlinx-serialization-runtime:$serialization_version"
 
     compile "io.ktor:ktor-server-core:$ktor_version"
     compile "io.ktor:ktor-server-netty:$ktor_version"
diff --git a/src/main/kotlin/Application.kt b/src/main/kotlin/Application.kt
index 260c2b4..b0510b4 100644
--- a/src/main/kotlin/Application.kt
+++ b/src/main/kotlin/Application.kt
@@ -13,6 +13,9 @@ import kotlinx.html.ATarget
 import kotlinx.html.a
 import kotlinx.html.body
 import kotlinx.html.div
+import kotlinx.serialization.Serializable
+import kotlinx.serialization.UnstableDefault
+import kotlinx.serialization.json.Json
 
 
 fun main() {
@@ -42,4 +45,16 @@ suspend fun mainPage(call: ApplicationCall) = call.respondHtml {
     }
 }
 
-fun apiCall() = """{"id":1,"name":"test entity"}"""
+@UnstableDefault
+fun apiCall() = Json.stringify(ApiEntity.serializer(), entity)
+
+val entity = ApiEntity(
+    id = 1,
+    name = "test entity"
+)
+
+@Serializable
+data class ApiEntity(
+    val id: Long,
+    val name: String
+)
```
Step-2-Add-gradle-wrapper
------------------------------
commit 983d901b48c0961ae42d623e1b90fcd88c562b97
Author: rainer <rainer@systemkern.com>
Date:   Wed Aug 28 12:40:01 2019 +0200

    Step 8: Add JSON serialization
    
    Since we do not want to manually write our JSON output, we are going to
    utilise a Kotlin's built in serialization capabilities.


```
diff --git a/build.gradle b/build.gradle
index abb3541..bcafcf7 100644
--- a/build.gradle
+++ b/build.gradle
@@ -6,6 +6,7 @@
  */
 buildscript {
     ext.kotlin_version = "1.3.41"
+    ext.serialization_version = "0.11.0"
     ext.ktor_version = '1.1.4'
     ext.kotlinx_html_version = "0.6.12"
 
@@ -16,11 +17,14 @@ buildscript {
 
     dependencies {
         classpath "org.jetbrains.kotlin:kotlin-gradle-plugin:$kotlin_version"
+        classpath "org.jetbrains.kotlin:kotlin-serialization:$kotlin_version"
     }
 }
 
 apply plugin: 'java'
 apply plugin: 'kotlin'
+apply plugin: 'kotlinx-serialization'
+
 
 // repositories for downloading application dependencies
 repositories {
@@ -30,6 +34,7 @@ repositories {
 
 dependencies {
     compile "org.jetbrains.kotlin:kotlin-stdlib:$kotlin_version"
+    compile "org.jetbrains.kotlinx:kotlinx-serialization-runtime:$serialization_version"
 
     compile "io.ktor:ktor-server-core:$ktor_version"
     compile "io.ktor:ktor-server-netty:$ktor_version"
diff --git a/src/main/kotlin/Application.kt b/src/main/kotlin/Application.kt
index 260c2b4..b0510b4 100644
--- a/src/main/kotlin/Application.kt
+++ b/src/main/kotlin/Application.kt
@@ -13,6 +13,9 @@ import kotlinx.html.ATarget
 import kotlinx.html.a
 import kotlinx.html.body
 import kotlinx.html.div
+import kotlinx.serialization.Serializable
+import kotlinx.serialization.UnstableDefault
+import kotlinx.serialization.json.Json
 
 
 fun main() {
@@ -42,4 +45,16 @@ suspend fun mainPage(call: ApplicationCall) = call.respondHtml {
     }
 }
 
-fun apiCall() = """{"id":1,"name":"test entity"}"""
+@UnstableDefault
+fun apiCall() = Json.stringify(ApiEntity.serializer(), entity)
+
+val entity = ApiEntity(
+    id = 1,
+    name = "test entity"
+)
+
+@Serializable
+data class ApiEntity(
+    val id: Long,
+    val name: String
+)
```
Step-3-Setup-gradle-for-kotlin-building
------------------------------
commit 983d901b48c0961ae42d623e1b90fcd88c562b97
Author: rainer <rainer@systemkern.com>
Date:   Wed Aug 28 12:40:01 2019 +0200

    Step 8: Add JSON serialization
    
    Since we do not want to manually write our JSON output, we are going to
    utilise a Kotlin's built in serialization capabilities.


```
diff --git a/build.gradle b/build.gradle
index abb3541..bcafcf7 100644
--- a/build.gradle
+++ b/build.gradle
@@ -6,6 +6,7 @@
  */
 buildscript {
     ext.kotlin_version = "1.3.41"
+    ext.serialization_version = "0.11.0"
     ext.ktor_version = '1.1.4'
     ext.kotlinx_html_version = "0.6.12"
 
@@ -16,11 +17,14 @@ buildscript {
 
     dependencies {
         classpath "org.jetbrains.kotlin:kotlin-gradle-plugin:$kotlin_version"
+        classpath "org.jetbrains.kotlin:kotlin-serialization:$kotlin_version"
     }
 }
 
 apply plugin: 'java'
 apply plugin: 'kotlin'
+apply plugin: 'kotlinx-serialization'
+
 
 // repositories for downloading application dependencies
 repositories {
@@ -30,6 +34,7 @@ repositories {
 
 dependencies {
     compile "org.jetbrains.kotlin:kotlin-stdlib:$kotlin_version"
+    compile "org.jetbrains.kotlinx:kotlinx-serialization-runtime:$serialization_version"
 
     compile "io.ktor:ktor-server-core:$ktor_version"
     compile "io.ktor:ktor-server-netty:$ktor_version"
diff --git a/src/main/kotlin/Application.kt b/src/main/kotlin/Application.kt
index 260c2b4..b0510b4 100644
--- a/src/main/kotlin/Application.kt
+++ b/src/main/kotlin/Application.kt
@@ -13,6 +13,9 @@ import kotlinx.html.ATarget
 import kotlinx.html.a
 import kotlinx.html.body
 import kotlinx.html.div
+import kotlinx.serialization.Serializable
+import kotlinx.serialization.UnstableDefault
+import kotlinx.serialization.json.Json
 
 
 fun main() {
@@ -42,4 +45,16 @@ suspend fun mainPage(call: ApplicationCall) = call.respondHtml {
     }
 }
 
-fun apiCall() = """{"id":1,"name":"test entity"}"""
+@UnstableDefault
+fun apiCall() = Json.stringify(ApiEntity.serializer(), entity)
+
+val entity = ApiEntity(
+    id = 1,
+    name = "test entity"
+)
+
+@Serializable
+data class ApiEntity(
+    val id: Long,
+    val name: String
+)
```
Step-4-Add-unit-tests-to-the-application
------------------------------
commit 983d901b48c0961ae42d623e1b90fcd88c562b97
Author: rainer <rainer@systemkern.com>
Date:   Wed Aug 28 12:40:01 2019 +0200

    Step 8: Add JSON serialization
    
    Since we do not want to manually write our JSON output, we are going to
    utilise a Kotlin's built in serialization capabilities.


```
diff --git a/build.gradle b/build.gradle
index abb3541..bcafcf7 100644
--- a/build.gradle
+++ b/build.gradle
@@ -6,6 +6,7 @@
  */
 buildscript {
     ext.kotlin_version = "1.3.41"
+    ext.serialization_version = "0.11.0"
     ext.ktor_version = '1.1.4'
     ext.kotlinx_html_version = "0.6.12"
 
@@ -16,11 +17,14 @@ buildscript {
 
     dependencies {
         classpath "org.jetbrains.kotlin:kotlin-gradle-plugin:$kotlin_version"
+        classpath "org.jetbrains.kotlin:kotlin-serialization:$kotlin_version"
     }
 }
 
 apply plugin: 'java'
 apply plugin: 'kotlin'
+apply plugin: 'kotlinx-serialization'
+
 
 // repositories for downloading application dependencies
 repositories {
@@ -30,6 +34,7 @@ repositories {
 
 dependencies {
     compile "org.jetbrains.kotlin:kotlin-stdlib:$kotlin_version"
+    compile "org.jetbrains.kotlinx:kotlinx-serialization-runtime:$serialization_version"
 
     compile "io.ktor:ktor-server-core:$ktor_version"
     compile "io.ktor:ktor-server-netty:$ktor_version"
diff --git a/src/main/kotlin/Application.kt b/src/main/kotlin/Application.kt
index 260c2b4..b0510b4 100644
--- a/src/main/kotlin/Application.kt
+++ b/src/main/kotlin/Application.kt
@@ -13,6 +13,9 @@ import kotlinx.html.ATarget
 import kotlinx.html.a
 import kotlinx.html.body
 import kotlinx.html.div
+import kotlinx.serialization.Serializable
+import kotlinx.serialization.UnstableDefault
+import kotlinx.serialization.json.Json
 
 
 fun main() {
@@ -42,4 +45,16 @@ suspend fun mainPage(call: ApplicationCall) = call.respondHtml {
     }
 }
 
-fun apiCall() = """{"id":1,"name":"test entity"}"""
+@UnstableDefault
+fun apiCall() = Json.stringify(ApiEntity.serializer(), entity)
+
+val entity = ApiEntity(
+    id = 1,
+    name = "test entity"
+)
+
+@Serializable
+data class ApiEntity(
+    val id: Long,
+    val name: String
+)
```
Step-5-Add-netty-HTTP-server
------------------------------
commit 983d901b48c0961ae42d623e1b90fcd88c562b97
Author: rainer <rainer@systemkern.com>
Date:   Wed Aug 28 12:40:01 2019 +0200

    Step 8: Add JSON serialization
    
    Since we do not want to manually write our JSON output, we are going to
    utilise a Kotlin's built in serialization capabilities.


```
diff --git a/build.gradle b/build.gradle
index abb3541..bcafcf7 100644
--- a/build.gradle
+++ b/build.gradle
@@ -6,6 +6,7 @@
  */
 buildscript {
     ext.kotlin_version = "1.3.41"
+    ext.serialization_version = "0.11.0"
     ext.ktor_version = '1.1.4'
     ext.kotlinx_html_version = "0.6.12"
 
@@ -16,11 +17,14 @@ buildscript {
 
     dependencies {
         classpath "org.jetbrains.kotlin:kotlin-gradle-plugin:$kotlin_version"
+        classpath "org.jetbrains.kotlin:kotlin-serialization:$kotlin_version"
     }
 }
 
 apply plugin: 'java'
 apply plugin: 'kotlin'
+apply plugin: 'kotlinx-serialization'
+
 
 // repositories for downloading application dependencies
 repositories {
@@ -30,6 +34,7 @@ repositories {
 
 dependencies {
     compile "org.jetbrains.kotlin:kotlin-stdlib:$kotlin_version"
+    compile "org.jetbrains.kotlinx:kotlinx-serialization-runtime:$serialization_version"
 
     compile "io.ktor:ktor-server-core:$ktor_version"
     compile "io.ktor:ktor-server-netty:$ktor_version"
diff --git a/src/main/kotlin/Application.kt b/src/main/kotlin/Application.kt
index 260c2b4..b0510b4 100644
--- a/src/main/kotlin/Application.kt
+++ b/src/main/kotlin/Application.kt
@@ -13,6 +13,9 @@ import kotlinx.html.ATarget
 import kotlinx.html.a
 import kotlinx.html.body
 import kotlinx.html.div
+import kotlinx.serialization.Serializable
+import kotlinx.serialization.UnstableDefault
+import kotlinx.serialization.json.Json
 
 
 fun main() {
@@ -42,4 +45,16 @@ suspend fun mainPage(call: ApplicationCall) = call.respondHtml {
     }
 }
 
-fun apiCall() = """{"id":1,"name":"test entity"}"""
+@UnstableDefault
+fun apiCall() = Json.stringify(ApiEntity.serializer(), entity)
+
+val entity = ApiEntity(
+    id = 1,
+    name = "test entity"
+)
+
+@Serializable
+data class ApiEntity(
+    val id: Long,
+    val name: String
+)
```
Step-6-Add-the-Kotlin-HTTP-DSL-and-mainPage
------------------------------
commit 983d901b48c0961ae42d623e1b90fcd88c562b97
Author: rainer <rainer@systemkern.com>
Date:   Wed Aug 28 12:40:01 2019 +0200

    Step 8: Add JSON serialization
    
    Since we do not want to manually write our JSON output, we are going to
    utilise a Kotlin's built in serialization capabilities.


```
diff --git a/build.gradle b/build.gradle
index abb3541..bcafcf7 100644
--- a/build.gradle
+++ b/build.gradle
@@ -6,6 +6,7 @@
  */
 buildscript {
     ext.kotlin_version = "1.3.41"
+    ext.serialization_version = "0.11.0"
     ext.ktor_version = '1.1.4'
     ext.kotlinx_html_version = "0.6.12"
 
@@ -16,11 +17,14 @@ buildscript {
 
     dependencies {
         classpath "org.jetbrains.kotlin:kotlin-gradle-plugin:$kotlin_version"
+        classpath "org.jetbrains.kotlin:kotlin-serialization:$kotlin_version"
     }
 }
 
 apply plugin: 'java'
 apply plugin: 'kotlin'
+apply plugin: 'kotlinx-serialization'
+
 
 // repositories for downloading application dependencies
 repositories {
@@ -30,6 +34,7 @@ repositories {
 
 dependencies {
     compile "org.jetbrains.kotlin:kotlin-stdlib:$kotlin_version"
+    compile "org.jetbrains.kotlinx:kotlinx-serialization-runtime:$serialization_version"
 
     compile "io.ktor:ktor-server-core:$ktor_version"
     compile "io.ktor:ktor-server-netty:$ktor_version"
diff --git a/src/main/kotlin/Application.kt b/src/main/kotlin/Application.kt
index 260c2b4..b0510b4 100644
--- a/src/main/kotlin/Application.kt
+++ b/src/main/kotlin/Application.kt
@@ -13,6 +13,9 @@ import kotlinx.html.ATarget
 import kotlinx.html.a
 import kotlinx.html.body
 import kotlinx.html.div
+import kotlinx.serialization.Serializable
+import kotlinx.serialization.UnstableDefault
+import kotlinx.serialization.json.Json
 
 
 fun main() {
@@ -42,4 +45,16 @@ suspend fun mainPage(call: ApplicationCall) = call.respondHtml {
     }
 }
 
-fun apiCall() = """{"id":1,"name":"test entity"}"""
+@UnstableDefault
+fun apiCall() = Json.stringify(ApiEntity.serializer(), entity)
+
+val entity = ApiEntity(
+    id = 1,
+    name = "test entity"
+)
+
+@Serializable
+data class ApiEntity(
+    val id: Long,
+    val name: String
+)
```
Step-7-Add-a-JSON-API-endpoint
------------------------------
commit 983d901b48c0961ae42d623e1b90fcd88c562b97
Author: rainer <rainer@systemkern.com>
Date:   Wed Aug 28 12:40:01 2019 +0200

    Step 8: Add JSON serialization
    
    Since we do not want to manually write our JSON output, we are going to
    utilise a Kotlin's built in serialization capabilities.


```
diff --git a/build.gradle b/build.gradle
index abb3541..bcafcf7 100644
--- a/build.gradle
+++ b/build.gradle
@@ -6,6 +6,7 @@
  */
 buildscript {
     ext.kotlin_version = "1.3.41"
+    ext.serialization_version = "0.11.0"
     ext.ktor_version = '1.1.4'
     ext.kotlinx_html_version = "0.6.12"
 
@@ -16,11 +17,14 @@ buildscript {
 
     dependencies {
         classpath "org.jetbrains.kotlin:kotlin-gradle-plugin:$kotlin_version"
+        classpath "org.jetbrains.kotlin:kotlin-serialization:$kotlin_version"
     }
 }
 
 apply plugin: 'java'
 apply plugin: 'kotlin'
+apply plugin: 'kotlinx-serialization'
+
 
 // repositories for downloading application dependencies
 repositories {
@@ -30,6 +34,7 @@ repositories {
 
 dependencies {
     compile "org.jetbrains.kotlin:kotlin-stdlib:$kotlin_version"
+    compile "org.jetbrains.kotlinx:kotlinx-serialization-runtime:$serialization_version"
 
     compile "io.ktor:ktor-server-core:$ktor_version"
     compile "io.ktor:ktor-server-netty:$ktor_version"
diff --git a/src/main/kotlin/Application.kt b/src/main/kotlin/Application.kt
index 260c2b4..b0510b4 100644
--- a/src/main/kotlin/Application.kt
+++ b/src/main/kotlin/Application.kt
@@ -13,6 +13,9 @@ import kotlinx.html.ATarget
 import kotlinx.html.a
 import kotlinx.html.body
 import kotlinx.html.div
+import kotlinx.serialization.Serializable
+import kotlinx.serialization.UnstableDefault
+import kotlinx.serialization.json.Json
 
 
 fun main() {
@@ -42,4 +45,16 @@ suspend fun mainPage(call: ApplicationCall) = call.respondHtml {
     }
 }
 
-fun apiCall() = """{"id":1,"name":"test entity"}"""
+@UnstableDefault
+fun apiCall() = Json.stringify(ApiEntity.serializer(), entity)
+
+val entity = ApiEntity(
+    id = 1,
+    name = "test entity"
+)
+
+@Serializable
+data class ApiEntity(
+    val id: Long,
+    val name: String
+)
```
Step-8-Add-JSON-serialization
------------------------------
commit 983d901b48c0961ae42d623e1b90fcd88c562b97
Author: rainer <rainer@systemkern.com>
Date:   Wed Aug 28 12:40:01 2019 +0200

    Step 8: Add JSON serialization
    
    Since we do not want to manually write our JSON output, we are going to
    utilise a Kotlin's built in serialization capabilities.


```
diff --git a/build.gradle b/build.gradle
index abb3541..bcafcf7 100644
--- a/build.gradle
+++ b/build.gradle
@@ -6,6 +6,7 @@
  */
 buildscript {
     ext.kotlin_version = "1.3.41"
+    ext.serialization_version = "0.11.0"
     ext.ktor_version = '1.1.4'
     ext.kotlinx_html_version = "0.6.12"
 
@@ -16,11 +17,14 @@ buildscript {
 
     dependencies {
         classpath "org.jetbrains.kotlin:kotlin-gradle-plugin:$kotlin_version"
+        classpath "org.jetbrains.kotlin:kotlin-serialization:$kotlin_version"
     }
 }
 
 apply plugin: 'java'
 apply plugin: 'kotlin'
+apply plugin: 'kotlinx-serialization'
+
 
 // repositories for downloading application dependencies
 repositories {
@@ -30,6 +34,7 @@ repositories {
 
 dependencies {
     compile "org.jetbrains.kotlin:kotlin-stdlib:$kotlin_version"
+    compile "org.jetbrains.kotlinx:kotlinx-serialization-runtime:$serialization_version"
 
     compile "io.ktor:ktor-server-core:$ktor_version"
     compile "io.ktor:ktor-server-netty:$ktor_version"
diff --git a/src/main/kotlin/Application.kt b/src/main/kotlin/Application.kt
index 260c2b4..b0510b4 100644
--- a/src/main/kotlin/Application.kt
+++ b/src/main/kotlin/Application.kt
@@ -13,6 +13,9 @@ import kotlinx.html.ATarget
 import kotlinx.html.a
 import kotlinx.html.body
 import kotlinx.html.div
+import kotlinx.serialization.Serializable
+import kotlinx.serialization.UnstableDefault
+import kotlinx.serialization.json.Json
 
 
 fun main() {
@@ -42,4 +45,16 @@ suspend fun mainPage(call: ApplicationCall) = call.respondHtml {
     }
 }
 
-fun apiCall() = """{"id":1,"name":"test entity"}"""
+@UnstableDefault
+fun apiCall() = Json.stringify(ApiEntity.serializer(), entity)
+
+val entity = ApiEntity(
+    id = 1,
+    name = "test entity"
+)
+
+@Serializable
+data class ApiEntity(
+    val id: Long,
+    val name: String
+)
```
