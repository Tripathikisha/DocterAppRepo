# DocterAppRepo

# DocterApp
    ### This project store the data of user managment system.

# Framwork and Language use in this Project

    Springboot
    java

# Dependencies

    SpringWeb
    Spring Boot Dev Tools
    LomBok
    Validation
    mySql driver

#Data Flow

    
    # DocerController :- In controller layer we handle CRUD operatiom by http request.
    
    ## DocterService :- The Service layer handles all business logics.
   ## Docter :- Docter class is defined here. Properties of  defined here.

# Data structure used in my project.

    In my Project ArraySet
    In my Project ArrayList.

Project Summery

## My project includes below properties
### public class Admin {

    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Integer adminId;
    private String adminName;

    @Pattern(regexp = ".*@hospital\\.admin\\.in$")
    private String adminEmail;
    private String adminPassword;

}

## public class Doctor {

    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Integer docId;
    private String  docName;
    private double  docFee;

    @Enumerated(value = EnumType.STRING)
    private Specialization docSpecialization;

    @Enumerated(value = EnumType.STRING)
    private Qualification docQualification;

    private String docContact;

    @OneToMany(mappedBy = "doctor")
    List<Appointment> appointments;


}

## public class Patient {


    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Integer patientId;
    private String patientName;

    @Email
    private String patientEmail;

    @Pattern(regexp = "^(?=.*[A-Za-z])(?=.*\\d)(?=.*[@#$!%])[A-Za-z\\d@#$!%]{8,}$\n")
    private String patientPassword;

    @Enumerated(value = EnumType.STRING)
    private Gender patientGender;

    @Enumerated(value = EnumType.STRING)
    private BloopGroup patientBloodGroup;


    @Size(min = 10,max = 10)
    @Pattern(regexp = "\\d+")
    private String patientContact;


    private LocalDateTime patientDateOFBirth;

    @OneToMany(mappedBy = "patient")
    List<Appointment> appointments;




}

## public class Appointment {

    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Integer appointmentId;
    private String  appointmentDesc;

    LocalDateTime appCreationTime;
    LocalDateTime appScheduleTime;


    @ManyToOne()
    @JoinColumn(name = "fk_patient_id")
    Patient patient;

    @ManyToOne()
    @JoinColumn(name = "fk_doc_id")
    Doctor doctor;


}

### ETC

