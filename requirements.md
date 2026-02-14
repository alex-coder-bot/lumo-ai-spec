# Requirements Document: Lumo Bounded Reasoning System

## Problem Statement

People struggle with decision-making not because they lack knowledge, but because they rarely examine their own reasoning before real-world consequences occur. Traditional learning platforms teach concepts or provide advice, but they don't create space for users to stress-test their own logic through systematic challenge.

Lumo addresses this by providing a bounded reasoning environment where users engage with realistic dilemmas and receive AI-generated counter-questions that surface assumptions, explore trade-offs, and challenge reasoning consistency—without providing solutions, advice, or evaluation.

## System Classification

**Lumo is NOT a chatbot.** It is a bounded reasoning system that runs structured, stateless sessions with automatic termination after a maximum of 4 AI probes.

## Target Users

**Primary Audience**: Young adults (ages 16-25) navigating life decisions in relationships, work, finances, and personal boundaries.

**User Characteristics**:
- Seeking to improve decision-making skills through practice
- Comfortable with mobile-first digital experiences
- Value privacy and autonomy over external guidance
- Prefer short, focused interactions over lengthy courses
- Want to explore reasoning without judgment or evaluation

## Core Objectives

1. **Enable Reasoning Practice**: Provide a safe environment for users to examine their decision-making logic through systematic challenge
2. **Maintain Bounded Sessions**: Enforce strict session limits (max 4 probes) with automatic termination to prevent open-ended conversation
3. **Preserve User Autonomy**: Never provide advice, solutions, or validation—only challenge reasoning through neutral questions
4. **Ensure Privacy**: Operate statelessly with no persistent memory between sessions and no storage of user responses
5. **Maintain Safety**: Detect crisis situations and provide appropriate resources without attempting intervention

## Functional Requirements

### 1. Session Management

#### 1.1 Anonymous Session Initiation
**User Story**: As a user, I want to start a reasoning session without creating an account so that I can maintain privacy and reduce friction.

**Acceptance Criteria**:
- User can access platform without authentication
- Session starts with maximum 2 interactions (clicks/taps)
- Unique session ID generated for each session
- No user profile or persistent identity required
- Session initialization completes within 2 seconds

#### 1.2 Bounded Session Structure
**User Story**: As a user, I want sessions to have clear boundaries so that I know when the interaction will end.

**Acceptance Criteria**:
- Each session consists of exactly: 1 dilemma + 1 user response + 2-4 AI probes + 1 reflection prompt
- Session automatically terminates after maximum 4 probes
- No option to extend or continue beyond probe limit
- Session duration capped at 10 minutes maximum
- Clear visual indicator of probe count (e.g., "Probe 2 of 4")

#### 1.3 Stateless Execution
**User Story**: As a user, I want each session to be independent so that my previous responses don't influence future interactions.

**Acceptance Criteria**:
- No conversation history retained between sessions
- No user behavioral tracking across sessions
- Each session starts fresh with no context from previous sessions
- Session data deleted immediately after completion
- No "resume session" functionality

#### 1.4 Session Termination
**User Story**: As a user, I want clear session endings so that I know when the interaction is complete.

**Acceptance Criteria**:
- Session automatically terminates when probe limit reached
- User can manually exit session at any time
- Safety triggers cause immediate termination
- Session timeout (10 minutes) causes automatic termination
- Clear "Session Complete" message displayed
- Option to start new session immediately available

### 2. Dilemma Presentation

#### 2.1 Realistic Scenario Selection
**User Story**: As a user, I want to engage with realistic life situations so that the practice feels relevant to my actual experiences.

**Acceptance Criteria**:
- Dilemmas drawn from realistic life skills categories (communication, conflict resolution, financial decisions, relationships, workplace, boundaries, ethics, time management)
- Scenarios appropriate for ages 16-25
- Each dilemma includes context, stakeholders, and decision point
- Dilemma presented within 1 second of session start
- No academic or theoretical scenarios

#### 2.2 Scenario Diversity
**User Story**: As a user, I want varied scenarios across sessions so that I don't encounter repetitive situations.

**Acceptance Criteria**:
- Selection algorithm prevents immediate repetition
- Scenarios distributed across multiple categories
- Difficulty levels vary appropriately
- Usage tracking ensures balanced distribution
- Minimum 50 unique scenarios in initial library

### 3. User Response Capture

#### 3.1 Free-Form Input
**User Story**: As a user, I want to respond in my own words so that I can express my reasoning naturally.

**Acceptance Criteria**:
- Text input supported (500 character limit)
- Voice input supported (converted to text)
- No forced multiple choice or structured responses
- Input validation prevents empty submissions
- Character count indicator displayed

#### 3.2 Input Moderation
**User Story**: As a platform operator, I want to filter inappropriate content so that the system remains safe and functional.

**Acceptance Criteria**:
- Toxicity detection blocks profanity, hate speech, harassment
- PII detection removes personal information before processing
- Spam and bot detection prevents abuse
- Inappropriate content triggers user feedback message
- All moderation events logged anonymously

### 4. AI Probe Generation

#### 4.1 Reasoning-Based Counter-Questions
**User Story**: As a user, I want AI questions that challenge my reasoning so that I can examine my assumptions and logic.

**Acceptance Criteria**:
- AI generates questions based solely on user's expressed reasoning
- Questions surface assumptions, explore trade-offs, or present alternative perspectives
- Questions reference user's own logic, not external information
- Each probe generated within 3 seconds
- Probes are open-ended questions, not statements

#### 4.2 Probe Limit Enforcement
**User Story**: As a user, I want sessions to end after a defined number of probes so that interactions remain bounded.

**Acceptance Criteria**:
- Maximum 4 probes per session (hard limit)
- Minimum 2 probes per session (unless early termination)
- Probe counter increments after each AI question
- Session automatically transitions to reflection after probe 4
- No exceptions or extensions to probe limit

#### 4.3 Progressive Depth
**User Story**: As a user, I want each probe to build on previous responses so that the reasoning challenge deepens over time.

**Acceptance Criteria**:
- Each probe considers previous user responses in session
- Probes avoid repeating the same question type
- Depth increases from surface assumptions to deeper values
- Context from all previous probes included in generation
- No circular questioning patterns

### 5. AI Behavior Constraints

#### 5.1 No Advice Rule
**User Story**: As a user, I want the AI to avoid giving advice so that I maintain autonomy over my decisions.

**Acceptance Criteria**:
- AI never uses prescriptive language ("you should", "you must", "I recommend")
- AI never suggests specific actions or solutions
- AI never provides guidance or recommendations
- All AI outputs are questions, not statements
- Automated rule checking rejects advice-containing probes

#### 5.2 No Evaluation Rule
**User Story**: As a user, I want the AI to avoid judging my responses so that I feel safe exploring my reasoning.

**Acceptance Criteria**:
- AI never labels responses as "right" or "wrong"
- AI never assigns scores, grades, or ratings
- AI never uses evaluative language ("good", "bad", "smart", "foolish")
- AI never compares user responses to ideal answers
- No performance metrics displayed to user

#### 5.3 No Persuasion Rule
**User Story**: As a user, I want the AI to remain neutral so that I'm not influenced toward particular viewpoints.

**Acceptance Criteria**:
- AI never attempts to change user's mind
- AI never uses leading questions
- AI never expresses value judgments
- AI maintains curious, exploratory tone
- No hidden agendas in questioning

#### 5.4 Neutral Questioning Rule
**User Story**: As a user, I want AI questions to be genuinely open-ended so that I can explore freely.

**Acceptance Criteria**:
- Questions are open-ended, not yes/no
- Tone is curious, not judgmental
- Focus on user's reasoning process, not outcomes
- Questions encourage exploration, not specific answers
- No rhetorical or loaded questions

#### 5.5 No Therapeutic Language
**User Story**: As a user, I want the AI to avoid simulating therapy so that boundaries remain clear.

**Acceptance Criteria**:
- AI never uses therapeutic techniques or language
- AI never attempts diagnosis or treatment
- AI never simulates empathy or emotional support
- AI maintains analytical distance
- No counseling or mental health intervention

### 6. Reflection Phase

#### 6.1 Self-Reflection Prompts
**User Story**: As a user, I want reflection prompts at the end so that I can consolidate my thinking.

**Acceptance Criteria**:
- Reflection phase automatically triggered after final probe
- Prompts encourage user to consider reasoning journey
- Prompts address both logical and emotional aspects
- No AI response to reflection (user reflection only)
- Reflection is optional, not required

#### 6.2 No Guidance in Reflection
**User Story**: As a user, I want reflection prompts to be open-ended so that I draw my own conclusions.

**Acceptance Criteria**:
- Reflection prompts are questions, not suggestions
- No "correct" reflection provided
- No summary of "what you learned"
- No prescriptive next steps
- User reflection remains private (not stored)

### 7. Safety and Crisis Detection

#### 7.1 Crisis Keyword Monitoring
**User Story**: As a platform operator, I want to detect crisis situations so that users receive appropriate resources.

**Acceptance Criteria**:
- System monitors for suicide ideation keywords
- System detects abuse disclosure language
- System identifies mental health crisis indicators
- Context-aware detection (not just keyword matching)
- Detection occurs in real-time during input processing

#### 7.2 Safe Exit Response
**User Story**: As a user in crisis, I want immediate access to appropriate resources so that I can get help.

**Acceptance Criteria**:
- Crisis detection triggers immediate session termination
- Clear crisis resources displayed (hotlines, text lines, websites)
- Resources localized to user's region when possible
- Compassionate, non-judgmental messaging
- No attempt at AI intervention or counseling

#### 7.3 Safety Event Logging
**User Story**: As a platform operator, I want to track safety events so that I can monitor system effectiveness.

**Acceptance Criteria**:
- Safety triggers logged anonymously
- No user responses or identity stored
- Incident category and timestamp recorded
- Aggregate metrics available for analysis
- Individual incidents not traceable to users

### 8. Privacy and Data Protection

#### 8.1 No Response Storage
**User Story**: As a user, I want my responses to remain private so that I can explore reasoning freely.

**Acceptance Criteria**:
- User responses never stored permanently
- Responses used only for probe generation within session
- All response data deleted after session completion
- No conversation history database
- No ability to retrieve past responses

#### 8.2 Anonymous Session Logs
**User Story**: As a platform operator, I want minimal session metadata so that I can improve the system while protecting privacy.

**Acceptance Criteria**:
- Only session metadata logged (ID, timestamp, dilemma ID, probe count, completion status, duration)
- No user responses logged
- No user identity or device information logged
- No location data collected
- Logs automatically deleted after 90 days

#### 8.3 No User Tracking
**User Story**: As a user, I want to avoid behavioral tracking so that my privacy is protected.

**Acceptance Criteria**:
- No cross-session user identification
- No behavioral profiling or pattern analysis
- No cookies or persistent identifiers
- No third-party tracking scripts
- Analytics aggregated only, never individual

#### 8.4 Data Deletion
**User Story**: As a user, I want assurance that my data is deleted so that I can trust the platform.

**Acceptance Criteria**:
- Session data deleted immediately after completion
- Anonymous logs deleted after 90 days (automatic TTL)
- No backup or archive of user responses
- Data deletion verifiable through system design
- GDPR/CCPA compliant by design

## Non-Functional Requirements

### 9. Performance

#### 9.1 Response Latency
**User Story**: As a user, I want fast responses so that the interaction feels natural.

**Acceptance Criteria**:
- Dilemma presentation: < 1 second
- AI probe generation: < 3 seconds
- API response time: < 500ms
- Total session duration: 5-8 minutes typical
- No loading delays between probes

#### 9.2 Concurrent Sessions
**User Story**: As a platform operator, I want to support many simultaneous users so that the system scales.

**Acceptance Criteria**:
- Support 1000+ concurrent sessions
- No performance degradation under load
- Auto-scaling based on demand
- Queue buffering during traffic spikes
- Graceful degradation if limits exceeded

#### 9.3 Token Efficiency
**User Story**: As a platform operator, I want to minimize LLM token usage so that costs remain low.

**Acceptance Criteria**:
- Maximum 150 tokens per probe generation
- Optimized prompt templates
- Context limited to current session only
- No redundant API calls
- Template probes used when appropriate

### 10. Reliability

#### 10.1 LLM Fallback Strategy
**User Story**: As a user, I want sessions to continue even if AI services fail so that my experience isn't disrupted.

**Acceptance Criteria**:
- Primary LLM: AWS Bedrock
- Fallback LLM: OpenAI GPT-4 or Google Gemini
- Template probes used if all LLMs fail
- Fallback occurs within 5 seconds
- User notified only if session cannot continue

#### 10.2 Graceful Degradation
**User Story**: As a user, I want clear error messages so that I understand what's happening.

**Acceptance Criteria**:
- System failures result in user-friendly messages
- Option to retry or start new session provided
- No technical error details exposed to users
- Session state preserved during temporary failures
- Automatic recovery when possible

#### 10.3 Uptime Target
**User Story**: As a user, I want the platform to be available when I need it.

**Acceptance Criteria**:
- 99.5% uptime target
- Planned maintenance communicated in advance
- Multi-region deployment for redundancy (future)
- Automatic failover for critical services
- Status page available for transparency

### 11. Security

#### 11.1 Input Validation
**User Story**: As a platform operator, I want to prevent malicious input so that the system remains secure.

**Acceptance Criteria**:
- All user input validated and sanitized
- SQL injection prevention
- XSS attack prevention
- Rate limiting per IP address (10 sessions/hour)
- Bot detection and blocking

#### 11.2 Data Encryption
**User Story**: As a user, I want my data encrypted so that it remains secure.

**Acceptance Criteria**:
- TLS encryption for all data in transit
- Encryption at rest for stored data (S3, DynamoDB)
- Secure key management (AWS Secrets Manager)
- No plaintext storage of sensitive data
- Regular security audits

#### 11.3 API Security
**User Story**: As a platform operator, I want secure API access so that unauthorized use is prevented.

**Acceptance Criteria**:
- API key authentication for mobile apps
- CORS configuration for web access
- Request signing for sensitive operations
- API rate limiting per key
- Regular key rotation

### 12. Accessibility

#### 12.1 Mobile Optimization
**User Story**: As a mobile user, I want a fully functional experience so that I can use the platform anywhere.

**Acceptance Criteria**:
- Responsive design for all screen sizes
- Touch-optimized interface
- Works on iOS and Android
- Progressive Web App (PWA) support
- Offline capability for cached content

#### 12.2 Voice Input Support
**User Story**: As a user, I want to respond by voice so that I can interact hands-free.

**Acceptance Criteria**:
- Voice input via device microphone
- Speech-to-text conversion
- Support for major languages (English initially)
- Fallback to text input if voice fails
- Clear voice recording indicator

#### 12.3 Screen Reader Compatibility
**User Story**: As a user with visual impairments, I want screen reader support so that I can access the platform.

**Acceptance Criteria**:
- Semantic HTML structure
- ARIA labels for interactive elements
- Keyboard navigation support
- High contrast mode available
- Text alternatives for visual elements

## Success Metrics

### 13. Engagement Metrics

#### 13.1 Session Completion Rate
**Definition**: Percentage of sessions that reach the reflection phase (not terminated early)

**Target**: > 80% completion rate

**Measurement**: (Completed sessions / Total sessions started) × 100

#### 13.2 Repeat Session Frequency
**Definition**: Average number of sessions per unique user (tracked anonymously via temporary identifiers)

**Target**: > 3 sessions per user within 30 days

**Measurement**: Total sessions / Unique session initiators (30-day window)

#### 13.3 Average Reasoning Depth
**Definition**: Average number of probes per completed session

**Target**: 3.5 probes average (indicating users engage deeply)

**Measurement**: Sum of probe counts / Number of completed sessions

### 14. Quality Metrics

#### 14.1 Rule Violation Rate
**Definition**: Percentage of AI probes that violate behavioral constraints (advice, evaluation, persuasion)

**Target**: < 5% violation rate

**Measurement**: (Rejected probes / Total probes generated) × 100

#### 14.2 Fallback Usage Rate
**Definition**: Percentage of probes using template fallbacks instead of LLM generation

**Target**: < 10% fallback usage

**Measurement**: (Template probes / Total probes) × 100

#### 14.3 Safety Trigger Rate
**Definition**: Percentage of sessions triggering crisis detection

**Target**: < 2% of sessions (monitoring metric, not optimization target)

**Measurement**: (Sessions with safety trigger / Total sessions) × 100

### 15. Performance Metrics

#### 15.1 Probe Generation Latency
**Definition**: Time from user response submission to AI probe display

**Target**: < 3 seconds (95th percentile)

**Measurement**: P95 latency across all probe generations

#### 15.2 Session Start Latency
**Definition**: Time from user clicking "Start Session" to dilemma display

**Target**: < 1 second (95th percentile)

**Measurement**: P95 latency across all session initiations

#### 15.3 Error Rate
**Definition**: Percentage of sessions experiencing technical errors

**Target**: < 1% error rate

**Measurement**: (Sessions with errors / Total sessions) × 100

## Out of Scope

The following are explicitly NOT part of Lumo's requirements:

- **User Accounts**: No authentication, profiles, or persistent user data
- **Conversation History**: No ability to review past sessions
- **Progress Tracking**: No scores, levels, achievements, or gamification
- **Social Features**: No sharing, commenting, or community interaction
- **Educational Content**: No lessons, courses, or instructional material
- **Personalization**: No adaptive difficulty or user preference learning
- **Therapeutic Services**: No counseling, diagnosis, or mental health treatment
- **Advice Generation**: No recommendations, solutions, or guidance
- **Long-form Conversation**: No open-ended dialogue beyond 4 probes
- **Memory Between Sessions**: No context retention across sessions

## Compliance Requirements

### 16. Privacy Regulations

#### 16.1 GDPR Compliance
**Acceptance Criteria**:
- Data minimization by design
- Right to deletion (automatic via TTL)
- No personal data processing without consent
- Privacy policy clearly communicated
- Data processing records maintained

#### 16.2 CCPA Compliance
**Acceptance Criteria**:
- No sale of personal information
- Clear privacy disclosures
- User rights respected
- Opt-out mechanisms available
- Annual compliance review

### 17. Content Moderation

#### 17.1 Age-Appropriate Content
**Acceptance Criteria**:
- All dilemmas reviewed for age-appropriateness (16-25)
- No explicit sexual content
- No graphic violence
- No illegal activity promotion
- Regular content audits

#### 17.2 Bias Mitigation
**Acceptance Criteria**:
- Diverse scenario representation
- Regular AI output audits for bias
- Inclusive language in all content
- Multiple perspectives represented
- Bias incident reporting mechanism

## Dependencies

### 18. External Services

#### 18.1 AWS Bedrock
**Purpose**: Primary LLM access for probe generation

**Criticality**: High (core functionality)

**Fallback**: OpenAI GPT-4 or Google Gemini

#### 18.2 AWS Lambda
**Purpose**: Serverless compute for all backend functions

**Criticality**: High (core infrastructure)

**Fallback**: None (AWS service dependency)

#### 18.3 DynamoDB
**Purpose**: Session state and dilemma storage

**Criticality**: High (data persistence)

**Fallback**: None (AWS service dependency)

#### 18.4 S3
**Purpose**: Analytics logs and static content storage

**Criticality**: Medium (non-critical for sessions)

**Fallback**: Local storage for critical content

## Assumptions

1. Users have internet connectivity during sessions
2. Users are comfortable with English language (initial release)
3. Users have modern web browsers or mobile devices
4. AWS services maintain advertised uptime and performance
5. LLM APIs remain available and cost-effective
6. Users understand the system is not providing advice or therapy
7. Crisis resources remain accessible and appropriate
8. Regulatory environment for AI systems remains stable

## Constraints

1. **Budget**: Operational costs must remain under $0.10 per session
2. **Technology**: Must use AWS services for production deployment
3. **Timeline**: MVP must be deployable within 3 months
4. **Team**: Development by small team (2-3 engineers)
5. **Compliance**: Must meet GDPR and CCPA requirements from launch
6. **Safety**: Zero tolerance for harmful AI outputs
7. **Privacy**: No compromise on user data protection
8. **Architecture**: Must be stateless and horizontally scalable
