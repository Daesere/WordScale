# WordScale

## Overview

WordScale is a content enhancement platform that transforms text-based media into richer formats. Its initial feature is an audiobook generator that converts written text into narrated audio using distinct character and narrator voices.

## Tech Stack

<!-- <div align="center">
  <a href="https://github-readme-tech-stack.vercel.app">
    <img src="https://github-readme-tech-stack.vercel.app/api/cards?title=WordScale+Tech+Stack&align=center&titleAlign=center&lineCount=2&bg=%234454af&badge=%23a3b2d2&border=%23000000&titleColor=%23000000&line1=rubyonrails%2Cruby+on+rails%2Cff0000%3Bpostgresql%2Cpsotresql%2C073f9f%3Bsidekiq%2Csidekiq%2C970000%3B&line2=rubyonrails%2CActive+storage%2Cff0000%3Brubyonrails%2Cactivejob%2Cff0000%3Breact%2Creact%2C0085ff%3Bruby%2Crspec%2Cff0000%3B" alt="WordScale Tech Stack" />

  </a>
</div>

<hr> -->


- **Backend:** Ruby on Rails, PostgreSQL
- **Background Processing:** ActiveJob, Sidekiq
- **Storage:** Active Storage
- **Frontend:** React
- **Testing:** RSpec

## Architecture

### Overview

This application uses Ruby on Rails as the orchestration layer for content enhancement workflows. Rails is responsible for domain modeling, request handling, background processing, and asset management, while AI generation is treated as an external service. This separation keeps the system simple, scalable, and easy to evolve.

### Core components

#### Rails Web Layer
Handles user requests, authentication, and exposes RESTful endpoints. Controllers are intentionally kept thin and delegate business logic to service objects.

#### Domain Models
Core models represent user-submitted content and its enhancements. Models are responsible for validations, relationships, and enforcing domain invariants.

#### Background Jobs
Long-running AI tasks are executed asynchronously using ActiveJob. Jobs track lifecycle states (pending, processing, completed, failed) and are retryable on transient failures.

#### AI Service Layer
All AI interactions are encapsulated in dedicated service objects. This layer is responsible for prompt construction, API calls, error handling, and translating external responses into internal domain objects.

#### Asset Storage
Generated assets are managed using Active Storage, with PostgreSQL serving as the system of record for metadata, relationships, and lifecycle state.

#### FrontEnd
A React-based frontend consumes the Rails API and is responsible for user interaction and progress visualization, allowing long-running AI tasks to be handled asynchronously without blocking the user experience.