import React, { useState } from 'react';
import { Brain, ChevronRight, BookOpen, Target, Lightbulb, Clock, FileText, CheckCircle2, ArrowRight } from 'lucide-react';

export default function CognitiveStyleAssessment() {
  const [stage, setStage] = useState('welcome'); // welcome, assessment, results, preparation
  const [currentQuestion, setCurrentQuestion] = useState(0);
  const [answers, setAnswers] = useState([]);
  const [cognitiveProfile, setCognitiveProfile] = useState(null);
  const [selectedTopic, setSelectedTopic] = useState('');

  // Psychometric questions based on cognitive psychology research
  // Measures: Visual/Verbal, Sequential/Global, Active/Reflective, Sensing/Intuitive
  const assessmentQuestions = [
    {
      id: 1,
      category: 'visual_verbal',
      question: "When learning something new, you prefer:",
      options: [
        { text: "Diagrams, charts, and visual representations", value: 'visual', score: 2 },
        { text: "Written explanations and text descriptions", value: 'verbal', score: 2 },
        { text: "A mix of both visual and written content", value: 'balanced', score: 0 }
      ]
    },
    {
      id: 2,
      category: 'visual_verbal',
      question: "When remembering information, you tend to recall:",
      options: [
        { text: "Pictures, images, or spatial layouts", value: 'visual', score: 2 },
        { text: "Words, phrases, or verbal explanations", value: 'verbal', score: 2 },
        { text: "Both equally well", value: 'balanced', score: 0 }
      ]
    },
    {
      id: 3,
      category: 'sequential_global',
      question: "When solving a problem, you prefer to:",
      options: [
        { text: "Follow a step-by-step logical sequence", value: 'sequential', score: 2 },
        { text: "See the big picture first, then fill in details", value: 'global', score: 2 },
        { text: "Switch between both approaches", value: 'balanced', score: 0 }
      ]
    },
    {
      id: 4,
      category: 'sequential_global',
      question: "When reading instructions, you:",
      options: [
        { text: "Read carefully from start to finish in order", value: 'sequential', score: 2 },
        { text: "Skim to understand the overall concept first", value: 'global', score: 2 },
        { text: "Do a combination of both", value: 'balanced', score: 0 }
      ]
    },
    {
      id: 5,
      category: 'active_reflective',
      question: "You understand things better when you:",
      options: [
        { text: "Try them out and experiment actively", value: 'active', score: 2 },
        { text: "Think them through quietly first", value: 'reflective', score: 2 },
        { text: "Balance both thinking and doing", value: 'balanced', score: 0 }
      ]
    },
    {
      id: 6,
      category: 'active_reflective',
      question: "In a learning environment, you prefer:",
      options: [
        { text: "Hands-on activities and practical exercises", value: 'active', score: 2 },
        { text: "Time to reflect and contemplate ideas", value: 'reflective', score: 2 },
        { text: "A mix of activities and reflection", value: 'balanced', score: 0 }
      ]
    },
    {
      id: 7,
      category: 'sensing_intuitive',
      question: "When learning, you prefer material that is:",
      options: [
        { text: "Concrete, practical, and fact-based", value: 'sensing', score: 2 },
        { text: "Abstract, theoretical, and concept-based", value: 'intuitive', score: 2 },
        { text: "A balance of both practical and theoretical", value: 'balanced', score: 0 }
      ]
    },
    {
      id: 8,
      category: 'sensing_intuitive',
      question: "You prefer tasks that involve:",
      options: [
        { text: "Following established methods and procedures", value: 'sensing', score: 2 },
        { text: "Innovation and discovering new approaches", value: 'intuitive', score: 2 },
        { text: "Both proven methods and creative solutions", value: 'balanced', score: 0 }
      ]
    },
    {
      id: 9,
      category: 'processing_speed',
      question: "When learning new material, you prefer to:",
      options: [
        { text: "Move quickly through content and review later", value: 'fast', score: 2 },
        { text: "Take your time and master each concept fully", value: 'deliberate', score: 2 },
        { text: "Adjust pace based on difficulty", value: 'adaptive', score: 0 }
      ]
    },
    {
      id: 10,
      category: 'social_learning',
      question: "You learn best when:",
      options: [
        { text: "Working independently at your own pace", value: 'individual', score: 2 },
        { text: "Collaborating and discussing with others", value: 'social', score: 2 },
        { text: "Combining individual work with group discussion", value: 'mixed', score: 0 }
      ]
    },
    {
      id: 11,
      category: 'detail_orientation',
      question: "When studying, you focus more on:",
      options: [
        { text: "Specific details and precise facts", value: 'detail', score: 2 },
        { text: "Overall patterns and general principles", value: 'holistic', score: 2 },
        { text: "Both details and general concepts", value: 'integrated', score: 0 }
      ]
    },
    {
      id: 12,
      category: 'structure_preference',
      question: "You prefer learning materials that are:",
      options: [
        { text: "Highly organized with clear structure", value: 'structured', score: 2 },
        { text: "Flexible and exploratory", value: 'flexible', score: 2 },
        { text: "Semi-structured with some flexibility", value: 'moderate', score: 0 }
      ]
    }
  ];

  const calculateCognitiveProfile = () => {
    const scores = {
      visual: 0,
      verbal: 0,
      sequential: 0,
      global: 0,
      active: 0,
      reflective: 0,
      sensing: 0,
      intuitive: 0,
      fast: 0,
      deliberate: 0,
      individual: 0,
      social: 0,
      detail: 0,
      holistic: 0,
      structured: 0,
      flexible: 0
    };

    answers.forEach((answer, index) => {
      const question = assessmentQuestions[index];
      const selectedOption = question.options.find(opt => opt.text === answer);
      if (selectedOption && selectedOption.value !== 'balanced' && selectedOption.value !== 'adaptive' && selectedOption.value !== 'mixed' && selectedOption.value !== 'integrated' && selectedOption.value !== 'moderate') {
        scores[selectedOption.value] += selectedOption.score;
      }
    });

    const profile = {
      learningModality: scores.visual > scores.verbal ? 'Visual' : scores.verbal > scores.visual ? 'Verbal' : 'Multimodal',
      processingStyle: scores.sequential > scores.global ? 'Sequential' : scores.global > scores.sequential ? 'Global' : 'Integrated',
      engagementStyle: scores.active > scores.reflective ? 'Active' : scores.reflective > scores.active ? 'Reflective' : 'Balanced',
      contentPreference: scores.sensing > scores.intuitive ? 'Concrete/Practical' : scores.intuitive > scores.sensing ? 'Abstract/Theoretical' : 'Versatile',
      pace: scores.fast > scores.deliberate ? 'Fast-paced' : scores.deliberate > scores.fast ? 'Deliberate' : 'Adaptive',
      socialPreference: scores.individual > scores.social ? 'Independent' : scores.social > scores.individual ? 'Collaborative' : 'Flexible',
      focusType: scores.detail > scores.holistic ? 'Detail-oriented' : scores.holistic > scores.detail ? 'Big-picture' : 'Comprehensive',
      structureNeed: scores.structured > scores.flexible ? 'High structure' : scores.flexible > scores.structured ? 'Exploratory' : 'Moderate structure',
      scores: scores
    };

    return profile;
  };

  const generatePersonalizedPreparation = (topic) => {
    if (!cognitiveProfile || !topic) return null;

    const prep = {
      topic: topic,
      overview: '',
      learningPath: [],
      studyTechniques: [],
      resources: [],
      schedule: [],
      tips: []
    };

    // Generate personalized overview
    prep.overview = `Based on your ${cognitiveProfile.learningModality} learning style and ${cognitiveProfile.processingStyle.toLowerCase()} processing approach, this preparation plan is tailored specifically for you.`;

    // Learning Path based on cognitive profile
    if (cognitiveProfile.processingStyle === 'Sequential') {
      prep.learningPath = [
        { step: 1, title: 'Foundation Concepts', description: 'Start with basic building blocks in a step-by-step manner', duration: '2-3 days' },
        { step: 2, title: 'Progressive Development', description: 'Build upon each concept systematically', duration: '4-5 days' },
        { step: 3, title: 'Advanced Applications', description: 'Master complex applications following logical progression', duration: '3-4 days' },
        { step: 4, title: 'Integration & Review', description: 'Connect all concepts in sequence', duration: '2 days' }
      ];
    } else if (cognitiveProfile.processingStyle === 'Global') {
      prep.learningPath = [
        { step: 1, title: 'Big Picture Overview', description: 'Understand the complete landscape of the topic first', duration: '1-2 days' },
        { step: 2, title: 'Key Concepts Exploration', description: 'Dive into major themes and connections', duration: '3-4 days' },
        { step: 3, title: 'Detail Deep-Dives', description: 'Fill in specific details within the framework', duration: '4-5 days' },
        { step: 4, title: 'Synthesis', description: 'Integrate all parts back into the whole picture', duration: '2 days' }
      ];
    } else {
      prep.learningPath = [
        { step: 1, title: 'Contextual Introduction', description: 'Balance overview with foundational details', duration: '2 days' },
        { step: 2, title: 'Iterative Learning', description: 'Alternate between concepts and applications', duration: '5-6 days' },
        { step: 3, title: 'Comprehensive Practice', description: 'Apply knowledge through varied exercises', duration: '3 days' },
        { step: 4, title: 'Review & Consolidation', description: 'Strengthen connections and fill gaps', duration: '2 days' }
      ];
    }

    // Study Techniques
    if (cognitiveProfile.learningModality === 'Visual') {
      prep.studyTechniques.push(
        { icon: '🎨', name: 'Mind Mapping', description: 'Create visual diagrams connecting concepts' },
        { icon: '📊', name: 'Flowcharts & Diagrams', description: 'Draw processes and relationships visually' },
        { icon: '🖼️', name: 'Color Coding', description: 'Use colors to categorize and remember information' },
        { icon: '📸', name: 'Visual Summaries', description: 'Convert text into infographics and visual notes' }
      );
    } else if (cognitiveProfile.learningModality === 'Verbal') {
      prep.studyTechniques.push(
        { icon: '✍️', name: 'Written Summaries', description: 'Write detailed notes in your own words' },
        { icon: '🗣️', name: 'Verbal Repetition', description: 'Explain concepts out loud to yourself' },
        { icon: '📝', name: 'Mnemonic Devices', description: 'Create word-based memory aids and acronyms' },
        { icon: '📖', name: 'Reading & Rewriting', description: 'Multiple passes through text with annotations' }
      );
    } else {
      prep.studyTechniques.push(
        { icon: '🎯', name: 'Dual Coding', description: 'Combine visual and verbal representations' },
        { icon: '🔄', name: 'Multi-format Notes', description: 'Use text, diagrams, and charts together' },
        { icon: '💡', name: 'Varied Resources', description: 'Mix videos, articles, and interactive content' },
        { icon: '🎭', name: 'Multiple Modalities', description: 'Engage different senses in learning' }
      );
    }

    if (cognitiveProfile.engagementStyle === 'Active') {
      prep.studyTechniques.push(
        { icon: '⚡', name: 'Practice Problems', description: 'Solve exercises immediately after learning' },
        { icon: '🛠️', name: 'Hands-on Projects', description: 'Apply concepts through real-world tasks' },
        { icon: '🎮', name: 'Interactive Learning', description: 'Use simulations and interactive tools' }
      );
    } else if (cognitiveProfile.engagementStyle === 'Reflective') {
      prep.studyTechniques.push(
        { icon: '🤔', name: 'Contemplative Study', description: 'Take time to think deeply about concepts' },
        { icon: '📔', name: 'Reflective Journaling', description: 'Write thoughts and connections regularly' },
        { icon: '⏸️', name: 'Spaced Repetition', description: 'Review material with deliberate pauses' }
      );
    }

    // Resources based on preferences
    if (cognitiveProfile.contentPreference === 'Concrete/Practical') {
      prep.resources = [
        { type: 'Tutorials', description: 'Step-by-step practical guides with real examples' },
        { type: 'Case Studies', description: 'Real-world applications and scenarios' },
        { type: 'Practice Exercises', description: 'Hands-on problems with immediate feedback' },
        { type: 'Templates & Checklists', description: 'Ready-to-use practical tools' }
      ];
    } else if (cognitiveProfile.contentPreference === 'Abstract/Theoretical') {
      prep.resources = [
        { type: 'Conceptual Frameworks', description: 'Theoretical models and principles' },
        { type: 'Research Papers', description: 'In-depth theoretical exploration' },
        { type: 'Thought Experiments', description: 'Abstract scenarios for deep thinking' },
        { type: 'Comparative Analysis', description: 'Exploring relationships between theories' }
      ];
    } else {
      prep.resources = [
        { type: 'Hybrid Materials', description: 'Mix of theory and practical application' },
        { type: 'Interactive Courses', description: 'Balance of concepts and hands-on practice' },
        { type: 'Problem-based Learning', description: 'Theoretical foundations with practical problems' },
        { type: 'Varied Content', description: 'Multiple formats for comprehensive understanding' }
      ];
    }

    // Study Schedule
    const totalDays = 12;
    if (cognitiveProfile.pace === 'Fast-paced') {
      prep.schedule = [
        { week: 'Week 1', focus: 'Intensive learning - Cover 60% of material', hours: '3-4 hours/day' },
        { week: 'Week 2', focus: 'Completion and advanced topics - Remaining 40%', hours: '2-3 hours/day' },
        { week: 'Ongoing', focus: 'Quick reviews and practice tests', hours: '1 hour/day' }
      ];
    } else if (cognitiveProfile.pace === 'Deliberate') {
      prep.schedule = [
        { week: 'Week 1', focus: 'Deep mastery of fundamentals - 30% of material', hours: '2-3 hours/day' },
        { week: 'Week 2', focus: 'Thorough understanding of core concepts - 40%', hours: '2-3 hours/day' },
        { week: 'Week 3-4', focus: 'Advanced concepts and comprehensive review - 30%', hours: '2 hours/day' }
      ];
    } else {
      prep.schedule = [
        { week: 'Week 1-2', focus: 'Flexible pacing based on difficulty', hours: '2-3 hours/day' },
        { week: 'Week 3', focus: 'Accelerate through familiar areas, slow for complex topics', hours: '2-4 hours/day' },
        { week: 'Week 4', focus: 'Review and reinforce weak areas', hours: '1-2 hours/day' }
      ];
    }

    // Personalized Tips
    prep.tips = [
      `Your ${cognitiveProfile.learningModality.toLowerCase()} preference means you should prioritize ${cognitiveProfile.learningModality === 'Visual' ? 'diagrams and visual aids' : 'written explanations and verbal repetition'}.`,
      `As a ${cognitiveProfile.processingStyle.toLowerCase()} learner, ${cognitiveProfile.processingStyle === 'Sequential' ? 'ensure you complete each step before moving to the next' : 'start by understanding the big picture before diving into details'}.`,
      `Your ${cognitiveProfile.engagementStyle.toLowerCase()} style works best with ${cognitiveProfile.engagementStyle === 'Active' ? 'hands-on practice and immediate application' : 'time for reflection and deep thinking'}.`,
      `${cognitiveProfile.socialPreference === 'Independent' ? 'Study in a quiet space where you can focus without distractions' : 'Join study groups or find a study partner for collaborative learning'}.`,
      `With ${cognitiveProfile.structureNeed.toLowerCase()} needs, ${cognitiveProfile.structureNeed === 'High structure' ? 'create detailed schedules and stick to organized plans' : 'allow flexibility in your learning approach and explore topics freely'}.`
    ];

    return prep;
  };

  const handleAnswer = (answer) => {
    const newAnswers = [...answers, answer];
    setAnswers(newAnswers);

    if (currentQuestion < assessmentQuestions.length - 1) {
      setCurrentQuestion(currentQuestion + 1);
    } else {
      // Assessment complete
      const profile = calculateCognitiveProfile();
      setCognitiveProfile(profile);
      setStage('results');
    }
  };

  const handleGeneratePreparation = () => {
    if (selectedTopic) {
      setStage('preparation');
    }
  };

  const preparation = generatePersonalizedPreparation(selectedTopic);

  // Welcome Screen
  if (stage === 'welcome') {
    return (
      <div className="min-h-screen bg-gradient-to-br from-indigo-50 via-purple-50 to-pink-50 p-6 flex items-center justify-center">
        <div className="max-w-3xl w-full">
          <div className="bg-white rounded-3xl shadow-2xl p-12 border-4 border-indigo-100">
            <div className="text-center mb-8">
              <div className="inline-block p-6 bg-gradient-to-br from-indigo-500 to-purple-600 rounded-full mb-6">
                <Brain size={64} className="text-white" />
              </div>
              <h1 className="text-5xl font-black mb-4 bg-gradient-to-r from-indigo-600 via-purple-600 to-pink-600 bg-clip-text text-transparent">
                Cognitive Style Assessment
              </h1>
              <p className="text-xl text-gray-600 leading-relaxed">
                Discover your unique learning profile through scientifically-designed psychometric questions
              </p>
            </div>

            <div className="bg-gradient-to-br from-indigo-50 to-purple-50 rounded-2xl p-8 mb-8 border-2 border-indigo-200">
              <h2 className="text-2xl font-bold text-indigo-900 mb-4">What You'll Discover:</h2>
              <div className="grid md:grid-cols-2 gap-4">
                <div className="flex items-start gap-3">
                  <CheckCircle2 className="text-indigo-600 flex-shrink-0 mt-1" size={20} />
                  <div>
                    <p className="font-semibold text-gray-800">Learning Modality</p>
                    <p className="text-sm text-gray-600">Visual, Verbal, or Multimodal</p>
                  </div>
                </div>
                <div className="flex items-start gap-3">
                  <CheckCircle2 className="text-purple-600 flex-shrink-0 mt-1" size={20} />
                  <div>
                    <p className="font-semibold text-gray-800">Processing Style</p>
                    <p className="text-sm text-gray-600">Sequential or Global thinking</p>
                  </div>
                </div>
                <div className="flex items-start gap-3">
                  <CheckCircle2 className="text-pink-600 flex-shrink-0 mt-1" size={20} />
                  <div>
                    <p className="font-semibold text-gray-800">Engagement Preference</p>
                    <p className="text-sm text-gray-600">Active or Reflective learning</p>
                  </div>
                </div>
                <div className="flex items-start gap-3">
                  <CheckCircle2 className="text-indigo-600 flex-shrink-0 mt-1" size={20} />
                  <div>
                    <p className="font-semibold text-gray-800">Content Type</p>
                    <p className="text-sm text-gray-600">Concrete or Abstract preference</p>
                  </div>
                </div>
              </div>
            </div>

            <div className="text-center">
              <button
                onClick={() => setStage('assessment')}
                className="group bg-gradient-to-r from-indigo-600 to-purple-600 text-white px-12 py-5 rounded-2xl text-xl font-bold hover:from-indigo-700 hover:to-purple-700 transition-all shadow-xl hover:shadow-2xl transform hover:scale-105 flex items-center gap-3 mx-auto"
              >
                Begin Assessment
                <ChevronRight className="group-hover:translate-x-1 transition-transform" size={24} />
              </button>
              <p className="text-sm text-gray-500 mt-4">Takes approximately 5 minutes • 12 questions</p>
            </div>
          </div>
        </div>
      </div>
    );
  }

  // Assessment Screen
  if (stage === 'assessment') {
    const question = assessmentQuestions[currentQuestion];
    const progress = ((currentQuestion + 1) / assessmentQuestions.length) * 100;

    return (
      <div className="min-h-screen bg-gradient-to-br from-indigo-50 via-purple-50 to-pink-50 p-6 flex items-center justify-center">
        <div className="max-w-3xl w-full">
          <div className="bg-white rounded-3xl shadow-2xl p-10 border-4 border-indigo-100">
            {/* Progress Bar */}
            <div className="mb-8">
              <div className="flex justify-between text-sm font-semibold text-indigo-600 mb-2">
                <span>Question {currentQuestion + 1} of {assessmentQuestions.length}</span>
                <span>{Math.round(progress)}%</span>
              </div>
              <div className="h-3 bg-indigo-100 rounded-full overflow-hidden">
                <div 
                  className="h-full bg-gradient-to-r from-indigo-600 to-purple-600 transition-all duration-500 rounded-full"
                  style={{ width: `${progress}%` }}
                />
              </div>
            </div>

            {/* Question */}
            <div className="mb-8">
              <h2 className="text-3xl font-bold text-gray-800 mb-6 leading-tight">
                {question.question}
              </h2>
            </div>

            {/* Options */}
            <div className="space-y-4">
              {question.options.map((option, index) => (
                <button
                  key={index}
                  onClick={() => handleAnswer(option.text)}
                  className="w-full text-left p-6 rounded-2xl border-3 border-gray-200 hover:border-indigo-500 hover:bg-indigo-50 transition-all group bg-white shadow-md hover:shadow-xl transform hover:scale-[1.02]"
                >
                  <div className="flex items-center gap-4">
                    <div className="w-8 h-8 rounded-full bg-indigo-100 group-hover:bg-indigo-600 flex items-center justify-center flex-shrink-0 transition-colors">
                      <span className="text-indigo-600 group-hover:text-white font-bold transition-colors">
                        {String.fromCharCode(65 + index)}
                      </span>
                    </div>
                    <p className="text-lg text-gray-700 group-hover:text-indigo-900 font-medium">
                      {option.text}
                    </p>
                  </div>
                </button>
              ))}
            </div>
          </div>
        </div>
      </div>
    );
  }

  // Results Screen
  if (stage === 'results') {
    return (
      <div className="min-h-screen bg-gradient-to-br from-indigo-50 via-purple-50 to-pink-50 p-6">
        <div className="max-w-5xl mx-auto">
          <div className="bg-white rounded-3xl shadow-2xl p-10 border-4 border-indigo-100 mb-6">
            <div className="text-center mb-10">
              <div className="inline-block p-6 bg-gradient-to-br from-green-500 to-emerald-600 rounded-full mb-6">
                <CheckCircle2 size={64} className="text-white" />
              </div>
              <h1 className="text-4xl font-black mb-4 bg-gradient-to-r from-indigo-600 to-purple-600 bg-clip-text text-transparent">
                Your Cognitive Profile
              </h1>
              <p className="text-xl text-gray-600">
                Here's what we learned about your unique learning style
              </p>
            </div>

            {/* Profile Grid */}
            <div className="grid md:grid-cols-2 gap-6 mb-10">
              <div className="bg-gradient-to-br from-blue-50 to-indigo-50 rounded-2xl p-6 border-2 border-blue-200">
                <div className="flex items-center gap-3 mb-3">
                  <div className="p-2 bg-blue-600 rounded-lg">
                    <BookOpen size={24} className="text-white" />
                  </div>
                  <h3 className="text-xl font-bold text-gray-800">Learning Modality</h3>
                </div>
                <p className="text-3xl font-black text-blue-600 mb-2">{cognitiveProfile.learningModality}</p>
                <p className="text-sm text-gray-600">
                  {cognitiveProfile.learningModality === 'Visual' && 'You learn best through images, diagrams, and visual representations'}
                  {cognitiveProfile.learningModality === 'Verbal' && 'You learn best through words, explanations, and written content'}
                  {cognitiveProfile.learningModality === 'Multimodal' && 'You effectively use both visual and verbal learning approaches'}
                </p>
              </div>

              <div className="bg-gradient-to-br from-purple-50 to-pink-50 rounded-2xl p-6 border-2 border-purple-200">
                <div className="flex items-center gap-3 mb-3">
                  <div className="p-2 bg-purple-600 rounded-lg">
                    <Target size={24} className="text-white" />
                  </div>
                  <h3 className="text-xl font-bold text-gray-800">Processing Style</h3>
                </div>
                <p className="text-3xl font-black text-purple-600 mb-2">{cognitiveProfile.processingStyle}</p>
                <p className="text-sm text-gray-600">
                  {cognitiveProfile.processingStyle === 'Sequential' && 'You process information step-by-step in a logical order'}
                  {cognitiveProfile.processingStyle === 'Global' && 'You prefer seeing the big picture before diving into details'}
                  {cognitiveProfile.processingStyle === 'Integrated' && 'You flexibly switch between detailed and holistic thinking'}
                </p>
              </div>

              <div className="bg-gradient-to-br from-green-50 to-emerald-50 rounded-2xl p-6 border-2 border-green-200">
                <div className="flex items-center gap-3 mb-3">
                  <div className="p-2 bg-green-600 rounded-lg">
                    <Lightbulb size={24} className="text-white" />
                  </div>
                  <h3 className="text-xl font-bold text-gray-800">Engagement Style</h3>
                </div>
                <p className="text-3xl font-black text-green-600 mb-2">{cognitiveProfile.engagementStyle}</p>
                <p className="text-sm text-gray-600">
                  {cognitiveProfile.engagementStyle === 'Active' && 'You learn best through hands-on practice and experimentation'}
                  {cognitiveProfile.engagementStyle === 'Reflective' && 'You learn best through contemplation and deep thinking'}
                  {cognitiveProfile.engagementStyle === 'Balanced' && 'You effectively balance action and reflection in learning'}
                </p>
              </div>

              <div className="bg-gradient-to-br from-orange-50 to-amber-50 rounded-2xl p-6 border-2 border-orange-200">
                <div className="flex items-center gap-3 mb-3">
                  <div className="p-2 bg-orange-600 rounded-lg">
                    <FileText size={24} className="text-white" />
                  </div>
                  <h3 className="text-xl font-bold text-gray-800">Content Preference</h3>
                </div>
                <p className="text-3xl font-black text-orange-600 mb-2">{cognitiveProfile.contentPreference}</p>
                <p className="text-sm text-gray-600">
                  {cognitiveProfile.contentPreference === 'Concrete/Practical' && 'You prefer practical, real-world applications and examples'}
                  {cognitiveProfile.contentPreference === 'Abstract/Theoretical' && 'You enjoy theoretical concepts and abstract thinking'}
                  {cognitiveProfile.contentPreference === 'Versatile' && 'You appreciate both practical and theoretical content'}
                </p>
              </div>

              <div className="bg-gradient-to-br from-rose-50 to-pink-50 rounded-2xl p-6 border-2 border-rose-200">
                <div className="flex items-center gap-3 mb-3">
                  <div className="p-2 bg-rose-600 rounded-lg">
                    <Clock size={24} className="text-white" />
                  </div>
                  <h3 className="text-xl font-bold text-gray-800">Learning Pace</h3>
                </div>
                <p className="text-3xl font-black text-rose-600 mb-2">{cognitiveProfile.pace}</p>
                <p className="text-sm text-gray-600">
                  {cognitiveProfile.pace === 'Fast-paced' && 'You prefer moving quickly through material'}
                  {cognitiveProfile.pace === 'Deliberate' && 'You prefer taking time to master each concept thoroughly'}
                  {cognitiveProfile.pace === 'Adaptive' && 'You adjust your pace based on content difficulty'}
                </p>
              </div>

              <div className="bg-gradient-to-br from-cyan-50 to-blue-50 rounded-2xl p-6 border-2 border-cyan-200">
                <div className="flex items-center gap-3 mb-3">
                  <div className="p-2 bg-cyan-600 rounded-lg">
                    <Brain size={24} className="text-white" />
                  </div>
                  <h3 className="text-xl font-bold text-gray-800">Social Preference</h3>
                </div>
                <p className="text-3xl font-black text-cyan-600 mb-2">{cognitiveProfile.socialPreference}</p>
                <p className="text-sm text-gray-600">
                  {cognitiveProfile.socialPreference === 'Independent' && 'You learn best when working on your own'}
                  {cognitiveProfile.socialPreference === 'Collaborative' && 'You thrive in group learning environments'}
                  {cognitiveProfile.socialPreference === 'Flexible' && 'You adapt well to both individual and group learning'}
                </p>
              </div>
            </div>

            {/* Generate Preparation Section */}
            <div className="bg-gradient-to-br from-indigo-50 to-purple-50 rounded-2xl p-8 border-2 border-indigo-200">
              <h2 className="text-2xl font-bold text-indigo-900 mb-4">Generate Your Personalized Study Plan</h2>
              <p className="text-gray-700 mb-6">
                Enter a topic you want to learn, and we'll create a customized preparation plan based on your cognitive profile.
              </p>
              <div className="flex gap-4">
                <input
                  type="text"
                  value={selectedTopic}
                  onChange={(e) => setSelectedTopic(e.target.value)}
                  placeholder="e.g., Python Programming, Data Science, Web Development..."
                  className="flex-1 px-6 py-4 rounded-xl border-2 border-indigo-300 focus:border-indigo-600 focus:outline-none text-lg"
                />
                <button
                  onClick={handleGeneratePreparation}
                  disabled={!selectedTopic}
                  className="bg-gradient-to-r from-indigo-600 to-purple-600 text-white px-8 py-4 rounded-xl font-bold hover:from-indigo-700 hover:to-purple-700 transition-all disabled:opacity-50 disabled:cursor-not-allowed flex items-center gap-2 shadow-lg hover:shadow-xl"
                >
                  Generate Plan
                  <ArrowRight size={20} />
                </button>
              </div>
            </div>
          </div>
        </div>
      </div>
    );
  }

  // Preparation Plan Screen
  if (stage === 'preparation' && preparation) {
    return (
      <div className="min-h-screen bg-gradient-to-br from-indigo-50 via-purple-50 to-pink-50 p-6">
        <div className="max-w-6xl mx-auto">
          {/* Header */}
          <div className="bg-white rounded-3xl shadow-2xl p-10 border-4 border-indigo-100 mb-6">
            <div className="flex items-center justify-between mb-6">
              <div>
                <h1 className="text-4xl font-black mb-2 bg-gradient-to-r from-indigo-600 to-purple-600 bg-clip-text text-transparent">
                  Your Personalized Learning Plan
                </h1>
                <p className="text-xl text-gray-600">For: {preparation.topic}</p>
              </div>
              <button
                onClick={() => setStage('results')}
                className="px-6 py-3 bg-gray-200 hover:bg-gray-300 rounded-xl font-semibold transition-colors"
              >
                ← Back to Profile
              </button>
            </div>
            <div className="bg-gradient-to-br from-blue-50 to-indigo-50 rounded-2xl p-6 border-2 border-blue-200">
              <p className="text-gray-700 text-lg">{preparation.overview}</p>
            </div>
          </div>

          {/* Learning Path */}
          <div className="bg-white rounded-3xl shadow-2xl p-10 border-4 border-purple-100 mb-6">
            <h2 className="text-3xl font-black mb-6 text-purple-900 flex items-center gap-3">
              <Target size={32} />
              Your Learning Path
            </h2>
            <div className="space-y-4">
              {preparation.learningPath.map((step) => (
                <div key={step.step} className="flex gap-6 items-start">
                  <div className="flex-shrink-0 w-12 h-12 bg-gradient-to-br from-purple-600 to-indigo-600 rounded-full flex items-center justify-center text-white font-bold text-xl">
                    {step.step}
                  </div>
                  <div className="flex-1 bg-gradient-to-br from-purple-50 to-indigo-50 rounded-2xl p-6 border-2 border-purple-200">
                    <h3 className="text-xl font-bold text-gray-800 mb-2">{step.title}</h3>
                    <p className="text-gray-600 mb-2">{step.description}</p>
                    <p className="text-sm text-purple-600 font-semibold">⏱️ Duration: {step.duration}</p>
                  </div>
                </div>
              ))}
            </div>
          </div>

          {/* Study Techniques */}
          <div className="bg-white rounded-3xl shadow-2xl p-10 border-4 border-green-100 mb-6">
            <h2 className="text-3xl font-black mb-6 text-green-900 flex items-center gap-3">
              <Lightbulb size={32} />
              Recommended Study Techniques
            </h2>
            <div className="grid md:grid-cols-2 gap-4">
              {preparation.studyTechniques.map((technique, index) => (
                <div key={index} className="bg-gradient-to-br from-green-50 to-emerald-50 rounded-2xl p-6 border-2 border-green-200">
                  <div className="flex items-start gap-4">
                    <span className="text-4xl">{technique.icon}</span>
                    <div>
                      <h3 className="text-lg font-bold text-gray-800 mb-1">{technique.name}</h3>
                      <p className="text-sm text-gray-600">{technique.description}</p>
                    </div>
                  </div>
                </div>
              ))}
            </div>
          </div>

          {/* Resources */}
          <div className="bg-white rounded-3xl shadow-2xl p-10 border-4 border-orange-100 mb-6">
            <h2 className="text-3xl font-black mb-6 text-orange-900 flex items-center gap-3">
              <BookOpen size={32} />
              Recommended Resources
            </h2>
            <div className="grid md:grid-cols-2 gap-4">
              {preparation.resources.map((resource, index) => (
                <div key={index} className="bg-gradient-to-br from-orange-50 to-amber-50 rounded-2xl p-6 border-2 border-orange-200">
                  <h3 className="text-lg font-bold text-gray-800 mb-2">{resource.type}</h3>
                  <p className="text-sm text-gray-600">{resource.description}</p>
                </div>
              ))}
            </div>
          </div>

          {/* Schedule */}
          <div className="bg-white rounded-3xl shadow-2xl p-10 border-4 border-blue-100 mb-6">
            <h2 className="text-3xl font-black mb-6 text-blue-900 flex items-center gap-3">
              <Clock size={32} />
              Study Schedule
            </h2>
            <div className="space-y-4">
              {preparation.schedule.map((period, index) => (
                <div key={index} className="bg-gradient-to-br from-blue-50 to-cyan-50 rounded-2xl p-6 border-2 border-blue-200">
                  <div className="flex justify-between items-start mb-2">
                    <h3 className="text-xl font-bold text-gray-800">{period.week}</h3>
                    <span className="text-sm font-semibold text-blue-600 bg-blue-100 px-4 py-2 rounded-full">
                      {period.hours}
                    </span>
                  </div>
                  <p className="text-gray-600">{period.focus}</p>
                </div>
              ))}
            </div>
          </div>

          {/* Personalized Tips */}
          <div className="bg-white rounded-3xl shadow-2xl p-10 border-4 border-pink-100">
            <h2 className="text-3xl font-black mb-6 text-pink-900 flex items-center gap-3">
              <Brain size={32} />
              Personalized Tips for Success
            </h2>
            <div className="space-y-4">
              {preparation.tips.map((tip, index) => (
                <div key={index} className="flex items-start gap-4 bg-gradient-to-br from-pink-50 to-rose-50 rounded-2xl p-6 border-2 border-pink-200">
                  <div className="flex-shrink-0 w-8 h-8 bg-pink-600 rounded-full flex items-center justify-center text-white font-bold">
                    {index + 1}
                  </div>
                  <p className="text-gray-700 text-lg">{tip}</p>
                </div>
              ))}
            </div>
          </div>
        </div>
      </div>
    );
  }

  return null;
}
