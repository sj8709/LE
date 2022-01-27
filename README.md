# LE
Lecture Evaluation edit oracle_DB


SQL

create table evaluation (
    evaluationID number(10) primary key,
    userID varchar2(20),
    lectureName varchar2(50),
    professorName varchar2(20),
    lectureYear number(10),
    semesterDivide varchar2(20),
    lectureDivide varchar2(10),
    evaluationTitle varchar2(50),
    evaluationContent varchar2(2048),
    totalScore varchar2(5),
    creditScore varchar2(5),
    comfortableScore varchar2(5),
    lectureScore varchar2(5),
    likeCount number(10)
);

create sequence evaluation_seq start with 1 increment by 1;

create or replace trigger evaluation_seq_tr
 before insert on evaluation for each row
 when (new.evaluationID is null)
begin
 select evaluation_seq.nextval into :new.evaluationID from dual;
end;
/

create table tb_user (
    userID varchar2(20),
    userPassword varchar2(64),
    userEmail varchar2(50),
    userEmailHash varchar2(64),
    userEmailChecked char(1)
    );
    
create table likey (
 userID varchar2(20) primary key,
 evaluationID number(10) primary key,
 userIP varchar2(50)
);
