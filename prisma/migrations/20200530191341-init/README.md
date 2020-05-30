# Migration `20200530191341-init`

This migration has been generated at 5/30/2020, 7:13:41 PM.
You can check out the [state of the schema](./schema.prisma) after the migration.

## Database Steps

```sql
CREATE TABLE "public"."User" (
"email" text  NOT NULL ,"id" SERIAL,"name" text   ,
    PRIMARY KEY ("id"))

CREATE TABLE "public"."Post" (
"authorId" integer   ,"content" text   ,"id" SERIAL,"published" boolean  NOT NULL DEFAULT false,"title" text  NOT NULL ,
    PRIMARY KEY ("id"))

CREATE UNIQUE INDEX "User.email" ON "public"."User"("email")

ALTER TABLE "public"."Post" ADD FOREIGN KEY ("authorId")REFERENCES "public"."User"("id") ON DELETE SET NULL  ON UPDATE CASCADE
```

## Changes

```diff
diff --git schema.prisma schema.prisma
migration 20200515225151-init..20200530191341-init
--- datamodel.dml
+++ datamodel.dml
@@ -3,9 +3,9 @@
 }
 datasource db {
   provider = "postgresql"
-  url = "***"
+  url      = "postgres://gblebxde:P9emq7VRChJn_osMQSJUYYisJCFJnXpV@balarama.db.elephantsql.com:5432/gblebxde"
 }
 model User {
   email String  @unique
```


