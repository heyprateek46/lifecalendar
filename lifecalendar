import React, { useState } from 'react';
import { Card, CardHeader, CardTitle, CardContent } from '@/components/ui/card';
import { Input } from '@/components/ui/input';
import { Button } from '@/components/ui/button';

const LifeCalendar = () => {
  const [age, setAge] = useState('');
  const [showVisualization, setShowVisualization] = useState(false);

  const WEEKS_IN_YEAR = 52;
  const TOTAL_YEARS = 80;
  const TOTAL_WEEKS = WEEKS_IN_YEAR * TOTAL_YEARS;

  const calculateWeeks = (currentAge) => {
    const weeksLived = Math.floor(currentAge * WEEKS_IN_YEAR);
    return weeksLived;
  };

  const handleSubmit = (e) => {
    e.preventDefault();
    setShowVisualization(true);
  };

  const renderWeeks = () => {
    const weeksLived = calculateWeeks(parseFloat(age));
    const weeks = [];

    for (let year = 0; year < TOTAL_YEARS; year++) {
      const yearWeeks = [];
      for (let week = 0; week < WEEKS_IN_YEAR; week++) {
        const weekIndex = year * WEEKS_IN_YEAR + week;
        const isLived = weekIndex < weeksLived;
        yearWeeks.push(
          <div
            key={weekIndex}
            className={`w-2 h-2 rounded-full m-0.5 ${
              isLived ? 'bg-blue-500' : 'bg-gray-200'
            }`}
            title={`Year ${year + 1}, Week ${week + 1}`}
          />
        );
      }
      weeks.push(
        <div key={year} className="flex">
          <div className="w-8 text-xs text-gray-500 flex items-center justify-end pr-2">
            {year + 1}
          </div>
          <div className="flex flex-wrap w-full">{yearWeeks}</div>
        </div>
      );
    }
    return weeks;
  };

  const Stats = () => {
    const weeksLived = calculateWeeks(parseFloat(age));
    const weeksRemaining = TOTAL_WEEKS - weeksLived;
    const percentageLived = ((weeksLived / TOTAL_WEEKS) * 100).toFixed(1);

    return (
      <div className="mt-4 space-y-2 text-sm text-gray-600">
        <p>Weeks lived: {weeksLived.toLocaleString()}</p>
        <p>Weeks remaining: {weeksRemaining.toLocaleString()}</p>
        <p>Life percentage: {percentageLived}%</p>
      </div>
    );
  };

  return (
    <Card className="w-full max-w-4xl">
      <CardHeader>
        <CardTitle>Life in Weeks</CardTitle>
      </CardHeader>
      <CardContent>
        <form onSubmit={handleSubmit} className="mb-6 flex gap-4">
          <Input
            type="number"
            value={age}
            onChange={(e) => setAge(e.target.value)}
            placeholder="Enter your age"
            className="w-32"
            step="0.1"
            min="0"
            max="80"
            required
          />
          <Button type="submit">Visualize</Button>
        </form>

        {showVisualization && age && (
          <div>
            <div className="overflow-x-auto">
              <div className="space-y-1">{renderWeeks()}</div>
            </div>
            <Stats />
          </div>
        )}
      </CardContent>
    </Card>
  );
};

export default LifeCalendar;
