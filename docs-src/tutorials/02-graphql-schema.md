## GrapQL Schema definition.

Also available along with <a href="https://uniroomy.co.uk:3003/api/graphiql" target="_blank">Visual UniRoomy GraphQL editor</a>


```
    schema {
      query: RootQueryType
      mutation: Mutation
    }
    
    """Represents possible achievement"""
    type Achievement {
      _id: ID
      name: String
      studentAchievements(skip: Int, limit: Int): [StudentAchievement]
    }
    
    input AchievementInput {
      name: String!
    }
    
    """Bedroom of a house"""
    type Bedroom {
      _id: ID
      house_id: ID
      name: String
      beds: Int
      baths: Int
      weekly_price: Float
      monthly_price: Float
      rating: Float
      contract_length: Int
      contract_starts: Date
      contract_ends: Date
      occupied: Boolean
      house(_id: ID): House
      bedroomPhotos(skip: Int, limit: Int): [BedroomPhoto]
    }
    
    input BedroomInput {
      house_id: ID!
      name: String
      beds: Int
      baths: Int
      weekly_price: Float
      monthly_price: Float
      rating: Float
      contract_length: Int
      contract_starts: Date
      contract_ends: Date
      occupied: Boolean
    }
    
    """Represents house photos"""
    type BedroomPhoto {
      _id: ID
      url: String
      bedroom_id: ID
      bedroom(_id: ID): Bedroom
    }
    
    input BedroomPhotoInput {
      url: String!
      bedroom_id: ID!
    }
    
    """Represents possible bill wich could be included to rent"""
    type Bill {
      _id: ID
      name: String
      houseBills(skip: Int, limit: Int): [HouseBill]
    }
    
    input BillInput {
      name: String!
    }
    
    """Category of element"""
    type Category {
      _id: ID
      name: String
      elements(skip: Int, limit: Int): [Element]
    }
    
    input CategoryInput {
      name: String!
    }
    
    """
    A date string, such as 2007-12-03, compliant with the `full-date` format
    outlined in section 5.6 of the RFC 3339 profile of the ISO 8601 standard for
    representation of dates and times using the Gregorian calendar.
    """
    scalar Date
    
    """
    A date-time string at UTC, such as 2007-12-03T10:15:30Z, compliant with the
    `date-time` format outlined in section 5.6 of the RFC 3339 profile of the ISO
    8601 standard for representation of dates and times using the Gregorian calendar.
    """
    scalar DateTime
    
    """
    Represents element. Element describes one of characteristics of a house.
    """
    type Element {
      _id: ID
      name: String
      category_id: ID
      element_kind_id: ID
      category(_id: ID): Category
      element_kind(_id: ID): ElementKind
      reviewHouseElements(skip: Int, limit: Int): [ReviewHouseElement]
      preferences(skip: Int, limit: Int): [Preference]
    }
    
    input ElementInput {
      name: String!
      category_id: ID!
      element_kind_id: ID!
    }
    
    """
    Represents element type. (used word "kind" instead of "type" because of entity type name collisions)
    """
    type ElementKind {
      _id: ID
      name: String
      range_from: Int
      range_to: Int
      elements(skip: Int, limit: Int): [Element]
      elementKindValueses(skip: Int, limit: Int): [ElementKindValues]
    }
    
    input ElementKindInput {
      name: String!
      range_from: Int
      range_to: Int
    }
    
    """Represents possible value of an element type"""
    type ElementKindValues {
      _id: ID
      element_kind_id: ID
      value: String
      element_kind(_id: ID): ElementKind
    }
    
    input ElementKindValuesInput {
      element_kind_id: ID!
      value: String
    }
    
    """Represents a possible fact about a house"""
    type Fact {
      _id: ID
      fact_group_id: ID
      name: String
      fact_group(_id: ID): FactGroup
      houseFacts(skip: Int, limit: Int): [HouseFact]
    }
    
    """Group of facts"""
    type FactGroup {
      _id: ID
      name: String
      facts(skip: Int, limit: Int): [Fact]
    }
    
    input FactGroupInput {
      name: String!
    }
    
    input FactInput {
      fact_group_id: ID!
      name: String!
    }
    
    """Represents a favorite house of a student"""
    type FavoriteHouse {
      _id: ID
      house_id: ID
      student_id: ID
      house(_id: ID): House
      student(_id: ID): Student
    }
    
    input FavoriteHouseInput {
      house_id: ID!
      student_id: ID!
    }
    
    """Represents house"""
    type House {
      _id: ID
      landlord_id: ID
      name: String
      description: String
      city: String
      street: String
      zip: String
      address: String
      bathes: Int
      rating: Float
      landlord(_id: ID): Landlord
      bedrooms(skip: Int, limit: Int): [Bedroom]
      houseUniversities(skip: Int, limit: Int): [HouseUniversity]
      reviews(skip: Int, limit: Int): [Review]
      houseFacts(skip: Int, limit: Int): [HouseFact]
      housePhotos(skip: Int, limit: Int): [HousePhoto]
      houseBills(skip: Int, limit: Int): [HouseBill]
      favoriteHouses(skip: Int, limit: Int): [FavoriteHouse]
    }
    
    """Represents a bill included to rent of a house"""
    type HouseBill {
      _id: ID
      house_id: ID
      bill_id: ID
      house(_id: ID): House
      bill(_id: ID): Bill
    }
    
    input HouseBillInput {
      house_id: ID!
      bill_id: ID!
    }
    
    """Represents fact about a house"""
    type HouseFact {
      _id: ID
      house_id: ID
      fact_id: ID
      house(_id: ID): House
      fact(_id: ID): Fact
    }
    
    input HouseFactInput {
      house_id: ID!
      fact_id: ID!
    }
    
    input HouseInput {
      landlord_id: ID!
      name: String
      description: String
      city: String
      street: String
      zip: String
      address: String
      bathes: Int
      rating: Float
    }
    
    """Represents house photos"""
    type HousePhoto {
      _id: ID
      url: String
      house_id: ID
      house(_id: ID): House
    }
    
    input HousePhotoInput {
      url: Upload!
      house_id: ID!
    }
    
    """For wich university the house is available for search"""
    type HouseUniversity {
      _id: ID
      house_id: ID
      university_id: ID
      time_by_car: Int
      time_by_walk: Int
      time_by_bus: Int
      house(_id: ID): House
      university(_id: ID): University
    }
    
    input HouseUniversityInput {
      house_id: ID!
      university_id: ID!
      time_by_car: Int
      time_by_walk: Int
      time_by_bus: Int
    }
    
    """Represents landlord"""
    type Landlord {
      _id: ID
      landlord_kind_id: ID
      company_name: String
      responsible_for_houses: Int
      responsible_for_beds: Int
      contact_name: String
      contact_number: String
      person(_id: ID): Person
      landlord_kind(_id: ID): LandlordKind
      houses(skip: Int, limit: Int): [House]
    }
    
    input LandlordInput {
      landlord_kind_id: ID
      company_name: String
      responsible_for_houses: Int
      responsible_for_beds: Int
      contact_name: String
      contact_number: String
      person: PersonInput
    }
    
    """
    Type of Landlord: 1 - Landlord, 2 - Property Developer, 3 - Letting Agency, 4 - University
    """
    type LandlordKind {
      _id: ID
      name: String
      landlords(skip: Int, limit: Int): [Landlord]
    }
    
    input LandlordKindInput {
      name: String!
    }
    
    type Mutation {
      addUniversity(input: UniversityInput): University
      updateUniversity(_id: ID, input: UniversityInput): University
      deleteUniversity(_id: ID): University
      addPerson(input: PersonInput): Person
      updatePerson(_id: ID, input: PersonInput): Person
      deletePerson(_id: ID): Person
      addTicket(input: TicketInput): Ticket
      updateTicket(_id: ID, input: TicketInput): Ticket
      deleteTicket(_id: ID): Ticket
      addRole(input: RoleInput): Role
      updateRole(_id: ID, input: RoleInput): Role
      deleteRole(_id: ID): Role
      addStudent(input: StudentInput): Student
      updateStudent(_id: ID, input: StudentInput): Student
      deleteStudent(_id: ID): Student
      addStatus(input: StatusInput): Status
      updateStatus(_id: ID, input: StatusInput): Status
      deleteStatus(_id: ID): Status
      addLandlord(input: LandlordInput): Landlord
      updateLandlord(_id: ID, input: LandlordInput): Landlord
      deleteLandlord(_id: ID): Landlord
      addLandlordKind(input: LandlordKindInput): LandlordKind
      updateLandlordKind(_id: ID, input: LandlordKindInput): LandlordKind
      deleteLandlordKind(_id: ID): LandlordKind
      addHouse(input: HouseInput): House
      updateHouse(_id: ID, input: HouseInput): House
      deleteHouse(_id: ID): House
      addHousePhoto(input: HousePhotoInput): HousePhoto
      updateHousePhoto(_id: ID, input: HousePhotoInput): HousePhoto
      deleteHousePhoto(_id: ID): HousePhoto
      addBedroomPhoto(input: BedroomPhotoInput): BedroomPhoto
      updateBedroomPhoto(_id: ID, input: BedroomPhotoInput): BedroomPhoto
      deleteBedroomPhoto(_id: ID): BedroomPhoto
      addFact(input: FactInput): Fact
      updateFact(_id: ID, input: FactInput): Fact
      deleteFact(_id: ID): Fact
      addFactGroup(input: FactGroupInput): FactGroup
      updateFactGroup(_id: ID, input: FactGroupInput): FactGroup
      deleteFactGroup(_id: ID): FactGroup
      addHouseFact(input: HouseFactInput): HouseFact
      updateHouseFact(_id: ID, input: HouseFactInput): HouseFact
      deleteHouseFact(_id: ID): HouseFact
      addHouseUniversity(input: HouseUniversityInput): HouseUniversity
      updateHouseUniversity(_id: ID, input: HouseUniversityInput): HouseUniversity
      deleteHouseUniversity(_id: ID): HouseUniversity
      addBedroom(input: BedroomInput): Bedroom
      updateBedroom(_id: ID, input: BedroomInput): Bedroom
      deleteBedroom(_id: ID): Bedroom
      addCategory(input: CategoryInput): Category
      updateCategory(_id: ID, input: CategoryInput): Category
      deleteCategory(_id: ID): Category
      addElement(input: ElementInput): Element
      updateElement(_id: ID, input: ElementInput): Element
      deleteElement(_id: ID): Element
      addElementKind(input: ElementKindInput): ElementKind
      updateElementKind(_id: ID, input: ElementKindInput): ElementKind
      deleteElementKind(_id: ID): ElementKind
      addElementKindValues(input: ElementKindValuesInput): ElementKindValues
      updateElementKindValues(_id: ID, input: ElementKindValuesInput): ElementKindValues
      deleteElementKindValues(_id: ID): ElementKindValues
      addPreference(input: PreferenceInput): Preference
      updatePreference(_id: ID, input: PreferenceInput): Preference
      deletePreference(_id: ID): Preference
      addAchievement(input: AchievementInput): Achievement
      updateAchievement(_id: ID, input: AchievementInput): Achievement
      deleteAchievement(_id: ID): Achievement
      addStudentAchievement(input: StudentAchievementInput): StudentAchievement
      updateStudentAchievement(_id: ID, input: StudentAchievementInput): StudentAchievement
      deleteStudentAchievement(_id: ID): StudentAchievement
      addReview(input: ReviewInput): Review
      updateReview(_id: ID, input: ReviewInput): Review
      deleteReview(_id: ID): Review
      addReviewHouseElement(input: ReviewHouseElementInput): ReviewHouseElement
      updateReviewHouseElement(_id: ID, input: ReviewHouseElementInput): ReviewHouseElement
      deleteReviewHouseElement(_id: ID): ReviewHouseElement
      addNotification(input: NotificationInput): Notification
      updateNotification(_id: ID, input: NotificationInput): Notification
      deleteNotification(_id: ID): Notification
      addBill(input: BillInput): Bill
      updateBill(_id: ID, input: BillInput): Bill
      deleteBill(_id: ID): Bill
      addHouseBill(input: HouseBillInput): HouseBill
      updateHouseBill(_id: ID, input: HouseBillInput): HouseBill
      deleteHouseBill(_id: ID): HouseBill
      addFavoriteHouse(input: FavoriteHouseInput): FavoriteHouse
      updateFavoriteHouse(_id: ID, input: FavoriteHouseInput): FavoriteHouse
      deleteFavoriteHouse(_id: ID): FavoriteHouse
    }
    
    """Represents notification of a person"""
    type Notification {
      _id: ID
      person_id: ID
      title: String
      subtitle: String
      full_description: String
      action: String
      read: Boolean
      person(_id: ID): Person
    }
    
    input NotificationInput {
      person_id: ID!
      title: String
      subtitle: String
      full_description: String
      action: String
      read: Boolean
    }
    
    """
    Represents person. Contains common fields for different roles (student/landlord).
    """
    type Person {
      _id: ID
      first_name: String
      last_name: String
      date_of_birth: Date
      email: String
      role_id: ID
      is_admin: Boolean
      created_at: DateTime
      updated_at: DateTime
      role(_id: ID): Role
      students(skip: Int, limit: Int): [Student]
      landlords(skip: Int, limit: Int): [Landlord]
      tickets(skip: Int, limit: Int): [Ticket]
      notifications(skip: Int, limit: Int): [Notification]
    }
    
    input PersonInput {
      first_name: String!
      last_name: String
      date_of_birth: Date
      email: String!
      is_admin: Boolean
      created_at: DateTime
      updated_at: DateTime
    }
    
    """Represents student`s preferred element"""
    type Preference {
      _id: ID
      student_id: ID
      element_id: ID
      element_weight: Float
      student(_id: ID): Student
      element(_id: ID): Element
    }
    
    input PreferenceInput {
      student_id: ID!
      element_id: ID!
      element_weight: Float
    }
    
    """Represents review of a house"""
    type Review {
      _id: ID
      student_id: ID
      house_id: ID
      description: String
      house_rating: Int
      created_at: Date
      student(_id: ID): Student
      house(_id: ID): House
      reviewHouseElements(skip: Int, limit: Int): [ReviewHouseElement]
    }
    
    """Represents an element of review of a house"""
    type ReviewHouseElement {
      _id: ID
      review_id: ID
      element_id: ID
      element_rating: String
      review(_id: ID): Review
      element(_id: ID): Element
    }
    
    input ReviewHouseElementInput {
      review_id: ID!
      element_id: ID!
      element_rating: String!
    }
    
    input ReviewInput {
      student_id: ID!
      house_id: ID!
      description: String!
      house_rating: Int!
      created_at: Date
    }
    
    """Represents UniRoomy person role. 1 - student, 2 - landlord"""
    type Role {
      _id: ID
      name: String
      persons(skip: Int, limit: Int): [Person]
    }
    
    input RoleInput {
      name: String!
    }
    
    type RootQueryType {
      university(_id: ID): University
      universities(skip: Int, limit: Int): [University]
      person(_id: ID): Person
      persons(skip: Int, limit: Int): [Person]
      ticket(_id: ID): Ticket
      tickets(skip: Int, limit: Int): [Ticket]
      role(_id: ID): Role
      roles(skip: Int, limit: Int): [Role]
      student(_id: ID): Student
      students(skip: Int, limit: Int): [Student]
      status(_id: ID): Status
      statuses(skip: Int, limit: Int): [Status]
      landlord(_id: ID): Landlord
      landlords(skip: Int, limit: Int): [Landlord]
      landlord_kind(_id: ID): LandlordKind
      landlord_kinds(skip: Int, limit: Int): [LandlordKind]
      house(_id: ID): House
      houses(skip: Int, limit: Int): [House]
      house_photo(_id: ID): HousePhoto
      house_photos(skip: Int, limit: Int): [HousePhoto]
      bedroom_photo(_id: ID): BedroomPhoto
      bedroom_photos(skip: Int, limit: Int): [BedroomPhoto]
      fact(_id: ID): Fact
      facts(skip: Int, limit: Int): [Fact]
      fact_group(_id: ID): FactGroup
      fact_groups(skip: Int, limit: Int): [FactGroup]
      house_fact(_id: ID): HouseFact
      house_facts(skip: Int, limit: Int): [HouseFact]
      house_university(_id: ID): HouseUniversity
      house_universities(skip: Int, limit: Int): [HouseUniversity]
      bedroom(_id: ID): Bedroom
      bedrooms(skip: Int, limit: Int): [Bedroom]
      category(_id: ID): Category
      categories(skip: Int, limit: Int): [Category]
      element(_id: ID): Element
      elements(skip: Int, limit: Int): [Element]
      element_kind(_id: ID): ElementKind
      element_kinds(skip: Int, limit: Int): [ElementKind]
      element_kind_values(_id: ID): ElementKindValues
      element_kind_valueses(skip: Int, limit: Int): [ElementKindValues]
      preference(_id: ID): Preference
      preferences(skip: Int, limit: Int): [Preference]
      achievement(_id: ID): Achievement
      achievements(skip: Int, limit: Int): [Achievement]
      student_achievement(_id: ID): StudentAchievement
      student_achievements(skip: Int, limit: Int): [StudentAchievement]
      review(_id: ID): Review
      reviews(skip: Int, limit: Int): [Review]
      review_house_element(_id: ID): ReviewHouseElement
      review_house_elements(skip: Int, limit: Int): [ReviewHouseElement]
      notification(_id: ID): Notification
      notifications(skip: Int, limit: Int): [Notification]
      bill(_id: ID): Bill
      bills(skip: Int, limit: Int): [Bill]
      house_bill(_id: ID): HouseBill
      house_bills(skip: Int, limit: Int): [HouseBill]
      favorite_house(_id: ID): FavoriteHouse
      favorite_houses(skip: Int, limit: Int): [FavoriteHouse]
    }
    
    """
    Represents student status: 1 - Not a Student, 2 - Prospective Student, 3 - Undergraduate Student, 4 - Graduated Student
    """
    type Status {
      _id: ID
      name: String
      students(skip: Int, limit: Int): [Student]
    }
    
    input StatusInput {
      name: String!
    }
    
    """Represents student"""
    type Student {
      _id: ID
      university_id: ID
      status_id: ID
      verified: Boolean
      tokens: Int
      person(_id: ID): Person
      university(_id: ID): University
      status(_id: ID): Status
      reviews(skip: Int, limit: Int): [Review]
      studentAchievements(skip: Int, limit: Int): [StudentAchievement]
      favoriteHouses(skip: Int, limit: Int): [FavoriteHouse]
      preferences(skip: Int, limit: Int): [Preference]
    }
    
    """Represents an achievement of a student"""
    type StudentAchievement {
      _id: ID
      student_id: ID
      achievement_id: ID
      created_at: DateTime
      student(_id: ID): Student
      achievement(_id: ID): Achievement
    }
    
    input StudentAchievementInput {
      student_id: ID!
      achievement_id: ID!
      created_at: DateTime
    }
    
    input StudentInput {
      university_id: ID
      status_id: ID
      verified: Boolean
      tokens: Int
      person: PersonInput
    }
    
    """Represent ticket created by person"""
    type Ticket {
      _id: ID
      message: String
      person_id: ID
      created_at: DateTime
      person(_id: ID): Person
    }
    
    input TicketInput {
      message: String!
      person_id: ID!
      created_at: DateTime
    }
    
    """Represents university."""
    type University {
      _id: ID
      name: String
      city: String
      houseUniversities(skip: Int, limit: Int): [HouseUniversity]
      students(skip: Int, limit: Int): [Student]
    }
    
    """Input fields for university"""
    input UniversityInput {
      name: String!
      city: String
    }
    
    """The `Upload` scalar type represents a file upload."""
    scalar Upload
    
```
