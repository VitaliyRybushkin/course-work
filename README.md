# course-work
Веб система выучи русский язык
Примерный скрипт бд:
CREATE TABLE "Teacher"(
    "id" INTEGER NOT NULL,
    "login" VARCHAR(255) NOT NULL,
    "password" VARCHAR(255) NOT NULL,
    "invite_id" INTEGER NOT NULL,
    "current_id" INTEGER NOT NULL,
    "fullname" VARCHAR(255) NOT NULL
);
ALTER TABLE
    "Teacher" ADD PRIMARY KEY("id");
CREATE TABLE "Invite_link"(
    "id" INTEGER NOT NULL,
    "invite" VARCHAR(255) NOT NULL
);
ALTER TABLE
    "Invite_link" ADD PRIMARY KEY("id");
CREATE TABLE "Student"(
    "id" INTEGER NOT NULL,
    "invite_id" INTEGER NOT NULL,
    "login" VARCHAR(255) NOT NULL,
    "password" VARCHAR(255) NOT NULL,
    "history_id" INTEGER NOT NULL,
    "fullname" VARCHAR(255) NOT NULL
);
ALTER TABLE
    "Student" ADD PRIMARY KEY("id");
CREATE TABLE "Task"(
    "id" INTEGER NOT NULL,
    "info" TEXT NOT NULL,
    "answer" TEXT NOT NULL
);
ALTER TABLE
    "Task" ADD PRIMARY KEY("id");
CREATE TABLE "Variant"(
    "id" INTEGER NOT NULL,
    "info" TEXT NOT NULL
);
ALTER TABLE
    "Variant" ADD PRIMARY KEY("id");
CREATE TABLE "Task_array"(
    "id" INTEGER NOT NULL,
    "task_id" INTEGER NOT NULL,
    "variant_id" INTEGER NOT NULL
);
ALTER TABLE
    "Task_array" ADD PRIMARY KEY("id");
CREATE TABLE "History"(
    "id" INTEGER NOT NULL,
    "student_id" INTEGER NOT NULL,
    "variant_id" INTEGER NOT NULL,
    "result" TEXT NOT NULL
);
ALTER TABLE
    "History" ADD PRIMARY KEY("id");
CREATE TABLE "Current_list"(
    "id" INTEGER NOT NULL,
    "teacher_id" INTEGER NOT NULL,
    "varriant_id" INTEGER NOT NULL,
    "status" VARCHAR(255) NOT NULL
);
ALTER TABLE
    "Current_list" ADD PRIMARY KEY("id");
ALTER TABLE
    "Student" ADD CONSTRAINT "student_invite_id_foreign" FOREIGN KEY("invite_id") REFERENCES "Invite_link"("id");
ALTER TABLE
    "Teacher" ADD CONSTRAINT "teacher_invite_id_foreign" FOREIGN KEY("invite_id") REFERENCES "Invite_link"("id");
ALTER TABLE
    "Task_array" ADD CONSTRAINT "task_array_task_id_foreign" FOREIGN KEY("task_id") REFERENCES "Task"("id");
ALTER TABLE
    "Task_array" ADD CONSTRAINT "task_array_variant_id_foreign" FOREIGN KEY("variant_id") REFERENCES "Variant"("id");
ALTER TABLE
    "Current_list" ADD CONSTRAINT "current_list_varriant_id_foreign" FOREIGN KEY("varriant_id") REFERENCES "Variant"("id");
ALTER TABLE
    "History" ADD CONSTRAINT "history_variant_id_foreign" FOREIGN KEY("variant_id") REFERENCES "Variant"("id");
